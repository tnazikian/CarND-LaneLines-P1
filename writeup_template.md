# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline Description

My pipeline consisted of 5 steps. First, I converted the images to HSV in order to filter out
white and yellow objects, and then converted it to grayscale. 
Next, I applied Gaussian smoothing to decrease the roughness of the lanes. 
Afterwards, I applied a Canny filter to find the edges of the lanes and applied a triangle-shaped mask that 
cropped out most objects that did not lie within the road. I then applied a Hough transform along the region 
of interest to detect any lines in the image. These lines were then applied to a custom function *draw_lines* 
that separated lines for the left and right lanes, and averaged the respective slopes and intercepts of the each.
These lines were then drawn on a blank frame as approximations of the positions of the left/right lanes. Finally,
a weighted image containing these lines and the original image is composed.
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

![alt text][out]


### 2. Identify potential shortcomings with your current pipeline

For the third video, the program has trouble detecting lines due to various sources of noise, 
such as: shadows, the hood of the car in the frame, and foliage next to the road. This was mitigated
by preprocessing the image through white and yellow color filters, and changing the region of interest.
Furthermore, the lines stray farther from the lanes during turns, as it can only plot straight lines. 


### 3. Suggest possible improvements to your pipeline

Currently, the program can only detect straight lines. This makes it difficult to trace lanes 
in sharp turns. In the future, a different program could be used that can trace curves as well
as straight lines. 
