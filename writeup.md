# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied a Gaussian blur filter with kernel size of 3. After that I ran a Canny edge detection, followed by an area of interest mask and Hough lines. Finally the results are overlapped to the originl Image. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by differentiating the slope of the o the lines: positive slopes for the right lane and negative for left. I filtered out slopes between -0.1 and 0.1 to try to remove horizontal or almost horizontal edges. Also I filtered out lines the goes over the half of the image, those greater for the left and those lower for the right ones. For every segment has been calculated the average with the saved one, then the final segment has been extended to the lower edge.   

![Example from single image](./test_images_output/1606612373.038971)

![Example from video](./test_images_output/1606612413.251953)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when lanes are very segmented or contrast is really low between asphalt and lane markings. 

Another shortcoming could be on turn, especially the more tight ones. Also changing the vehicle height, or camera position, could probably influence the outcome.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to leverage other filters to create more accurate masking and better filter markingss of interest.

Another potential improvement could be to better optimize the various parameters to take into account other factors in particular on masking and thresholds.
