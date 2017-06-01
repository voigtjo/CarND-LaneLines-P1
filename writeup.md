# **Finding Lane Lines on the Road** 




### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:

1. Grayscale the image
2. Define a kernel size and apply Gaussian smoothing
3. Define parameters for Canny edge detection and apply
4. Define region of interest using a four sided polygon to mask
5. Define parameters for Hough transformation and apply to identify lines
6. Draw the lines on the image


In order to draw one averaged and extrapolated left and one right lines of the lane I defined a function average_extrapolate_lines() which is called from draw_lines() function. This function has the following three process steps:

1. Loop through all lines, calculate slope and y-intercept and calculate average slope and y-intercept for all lines whose absolute value of the slope exceeds a certain minimum value
2. Calculate the intersection of the straight line equation with the bottom and the top of the region of interest
3. Determine the left and right limit-lines of the lanes and return these two as the new list of lines




### 2. Identify potential shortcomings with your current pipeline

The pipeline has successfully been applied to two videos. But in the third exercise, the algorithm stops. 

That is, the algorithm is not yet applicable in realistic situation.

Curves, in particular sharp curves, changing spawning conditions, for example shadows, interruptions and crossings,  have not yet been considered and lead to breakdowns and errors.


### 3. Suggest possible improvements to your pipeline

Patterns to be expected include "straight road", "curve", "shadow", "darkness", "crossroads", "other vehicles", "other road users" and many more.

And artifacts as such have to be recognized and treated robustly.

Unlike in an image processing, the video must be accompanied by the history and changes to the previous frames identified.