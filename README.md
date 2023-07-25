# Frontend Mentor - Order summary card solution

This is a solution to the [Order summary card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/order-summary-component-QlPmajDUj). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)


## Overview

### The challenge

Users should be able to:

- See hover states for interactive elements

### Screenshot

![](Screenshot%202023-07-25%20at%2012-59-22%20Order%20Summary.png)


### Links

- Live Site URL: [Netlify web site](https://rj-fem-order-summary.netlify.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow
- Sass


### What I learned

#### HTML Aria-label

This is a very useful html attribute because it allows to highlight the semantic function of an element, improving the accessibility of the site.

#### CSS Reset

I recently learned about the existence of css resets and its great importance, in short it has helped me avoid many common problems during the application of css styles.

The reset file I used in this project is a mix of resets from various sources.

Here you can find the corresponding links.
[CSS reset resources](#css-resets-resources)

#### CSS Utilty classes

I'm not used to using them yet, but they certainly help a bit to avoid code repetition.

#### SASS Mixins

They are probably the most important concept that I have learned recently, and that is that they have been very helpful for me to write certain snippets of css code in a much more efficient and comfortable way.

In this project I mainly used them to automatically define global variables and to write media queries and some pseudo-classes like hover and focus-visible.

This is a mixin that allows the automatic generation of color variables based on a map located in the _abstracts/_colors.scss file, I got the code from a Kevin Powell video on youtube that you can watch here -> [Sass Resources](#sass-resources).

```scss
@mixin createVarSection-nested($dictionary, $prefix, $dictionaryName){
    /*

    #{$dictionaryName} 
    */
    @each $category, $sub-dictionary in $dictionary{
        /* #{$category} */
        @each $key, $value in $sub-dictionary{
            @if $value != "" {
                --#{$prefix}-#{$category}-#{$key}: #{$value};
            }
        }
    }
}
```

Based on this code I developed a second version, this time for a simple map (not nested), however, this one has an additional argument called $remSizesType which enables the conversion of pixels to rem for those variables that require it, for example the size variables or the font sizes, in this way it is possible to define the values in pixels inside the map (which is more intuitive) and the mixin will convert them to rem to create the variables in the css file.

```scss
@mixin createVarSection($dictionary, $prefix, $dictionaryName, $oneLineLabel:false, $remSizesType: false, $quotes:false){
    @if $oneLineLabel == true {
        /* #{$dictionaryName} */
    }@else{
        /* 

        #{$dictionaryName} 
        */
    }
    @each $key, $value in $dictionary{
        @if $value != "" and $value != 0 {
            @if $remSizesType == true {
                $remConversion: calc($value / 16);
                $srtVar: inspect($remConversion);
                $labelIndentation: stringRepeat("-", calc(8 - str-length($srtVar)));
                --#{$prefix}-#{$key}: #{$remConversion}rem; /* #{$labelIndentation} #{$value}px */
            }@else{
                @if $quotes == true {
                    --#{$prefix}-#{$key}: "#{$value}", sans-serif;
                }@else{
                    --#{$prefix}-#{$key}: #{$value};
                }
            }
        }
    }
}
```

Feel free to use them if you find them useful 😉



### Continued development

I keep learning new css concepts to apply them during layout design, I am very interested in improving my skills, also I want to learn more about html accessibility and new tools and frameworks to organize and write my css code in a more efficient way.



### Useful resources

#### CSS Resets resources

These are the resources on which I based to create my customized CSS reset file:

- [CSS Reset by Andy Bell](https://andy-bell.co.uk/a-modern-css-reset/) I found this resource in a video tutorial by Kevin Powell on YouTube, in which he made some modifications that I also used in my own version. You can watch the video [here](https://youtu.be/h3bTwCqX4ns?t=820).
- [CSS Reset by Eduardo Fierro](https://www.youtube.com/watch?v=Foieq2jTajE&list=PLJpymL0goBgHH9APAeYt5ytE9eT4-lFvE&index=2&ab_channel=EduardoFierro) - (This content is in Spanish)

#### SASS Resources

- [Generate custom props & utility classes with Sass - by Kevin Powell](https://www.youtube.com/watch?v=gP8yFWCTr7Q&ab_channel=KevinPowell) - This is the video where I find the mixin code.

## Author

- Website - [Add your name here](https://www.your-site.com)
- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
- Twitter - [@yourusername](https://www.twitter.com/yourusername)
