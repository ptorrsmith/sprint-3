# Sprint 3 - Skeleton
## Q. What happens to the layout when you resize the screen to less than 550 px. 
When I narrow the screen to below 500px, the image becomes a single image of the phone (not the double/layered image on larger sizes) shrinks and the text sizes also shrink.  
 ## Q. How do you think that works?

This will be done through a combination of factors:
1. Including the link to the Skeleton stylesheets in the `<head>` section:  
  `<link rel="stylesheet" href="../../dist/css/normalize.css">`  
  Note: The above `link` tag is not actually a Skeleton stylesheet, just a helper stylesheet to help with cross-browser compatability)  
  `<link rel="stylesheet" href="../../dist/css/skeleton.css">`  
  and a link to our own stylesheet(s):  
  `<link rel="stylesheet" href="css/custom.css">`

1. linking to JQuery (required??):  
`<script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>`

1. In the HTML, include a "viewport" meta attribute in the `<head>` section as such:  
`<meta name="viewport" content="width=device-width, initial-scale=1">`  
as this will make the browser viewport size available to the stylesheet media queries and Javascript (???)

1. Then in our `custom.css` there are a number of "Media Queries" such as:  

    ```css
    /* Bigger than 550 */`
    @media (min-width: 550px) {
    .hero {
        padding-bottom: 12rem;
        text-align: left;
        height: 165px;  
    }
    */ extra .class styles here /*`  
    }
    ```
    which advise additional styles to apply if conditions (width is at least 550px).  

    _However_ it's worth noting that, as is advised good _"Mobile First"_ good practice, **the default (base) styles should be for the smallest viewport** (in this case anything under 550px), and then the `@media (condition-property: condition-value) {}` media query sections are used to accomodate and advise the styles to apply to larger browser viewport sizes.  See [the Queries section of the Skeleton documentation for a brief overview](http://getskeleton.com/#queries)


1. Specifically to make the second image not show on smaller devices, the **base** (not inside a media query conditional section) CSS in our `custom.css` file states

    ```css
    .phone + .phone {  
    display: none;  
    }
    ```
    which hides the element of class "phone" if it directly follows another element of class "phone". So the second (under) image does not show by default.  

    But then later in the `custom.css`, there are media queries which are used if the viewport is larger, and has the second image then showing:  

    ```css
    /* Bigger than 550 */
    @media (min-width: 550px) {
    .section {
        padding: 12rem 0 11rem;
    }
    .hero {
        padding-bottom: 12rem;
        text-align: left;
        height: 165px;
    }
    .phone {
        position: absolute;
        top: -7rem;
        right: 3rem;
        max-height: 362px;
        z-index: 3;
    }
    .phone + .phone {
        top: -6rem;
        display: block;
        max-width: 73.8%;
        right: 0;
        z-index: 2;
        max-height: 338px;
    }
    .hero-heading {
        font-size: 2.4rem;
    }
    }
    ```
    Notice the `.phone + .phone {}` class selector tells the browser to use `display: block;` which overrides the base CSS for this selector of `display: none;`

    > Note: The Skeleton CSS file has no defined styles for various viewport sizes.  It  has some recommended media query breakpoint sizes defined, but does not define any styles for them.  We are expected to add our own styles for larger viewports in our `custom.css`

    ```css  
    /* Media Queries
    –––––––––––––––––––––––––––––––––––––––––––––––––– */
    /*
    Note: The best way to structure the use of media queries is to create the queries
    near the relevant code. For example, if you wanted to change the styles for buttons
    on small devices, paste the mobile query code up in the buttons section and style it
    there.
    */


    /* Larger than mobile */
    @media (min-width: 400px) {}

    /* Larger than phablet (also point when grid becomes active) */
    @media (min-width: 550px) {}

    /* Larger than tablet */
    @media (min-width: 750px) {}

    /* Larger than desktop */
    @media (min-width: 1000px) {}

    /* Larger than Desktop HD */
    @media (min-width: 1200px) {}
    ```


    Notice the above extract from the `skeleton.css` stylesheet has defined a viewport breakpoint of width >= 400px, however in this example, our `custom.css` did not define a breakpoint for this, and only has styles defined for viewports of 550px or greater.

### Conclusion
So it appears that the main "look different at different viewport sizes" is only a result of our own media queries and their styles defined in our `custom.css` file and not something "out of the box" with Skeleton.





  
