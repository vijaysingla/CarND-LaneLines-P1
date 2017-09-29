
# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work in  a written report


[//]: # (Image References)

[image1]: ./test_images_output/CannyEdge.png "CannyEdge"
[image2]: ./test_images_output/RegionOfInterest.png "CannyEdge"
[image3]: ./test_images_output/HoughOutputWithExtrapolatedLines.png "HoughOutput"
[image4]: ./test_images_output/LanePlotting.png "LanePlotting"
[image5]: ./test_images_output/solidWhiteCurve.jpg
[image6]: ./test_images_output/solidWhiteRight.jpg
[image7]: ./test_images_output/solidYellowCurve.jpg
[image8]: ./test_images_output/solidYellowCurve2.jpg
[image9]: ./test_images_output/solidYellowLeft.jpg
[image10]: ./test_images_output/whiteCarLaneSwitch.jpg


---

### Reflection

### 1. Description 

My pipeline consisted of the following steps. First, I converted the images to grayscale, then I used the gaussian filter on it to filter the image. After that, I used canny edge detection to edges in the image as shown below

![alt text][image1]

Canny edge detection method also yield edges other than lane edges. I used a region of interest to eliminate unwanted edges. to produce a masked image as shown below
![alt text][image2]

After that, I used hough transforamtion method to get the potential line coordinates passing through the masked image. 
I  categorized those lines into two sections based on sign of line slope. Positive slope coordianted formed the right lane and Negative slope coordinates formed the left lane. After that, I used polyfit to find the best single line fit for  right as well left lane. I used the slope and intersect obtained using polyfit method to draw line through right and left lane as shown below

![alt text][image3]

I used the extrapolated hough line output and merged it with original image to create red color lines on the top of the original image as shown belo 

![alt text][image4]

I used the mehtod described above and used it on the all 6 test images and saved results in the test_images_output folder and showing the results here 

![alt text][image5]![alt text][image6]![alt text][image7]![alt text][image8]![alt text][image9]![alt text][image10]


### 2. Potential shortcomings with my current pipeline

One potential shortcoming is the sensitivity of region of interest to my solution. If the camera captures image with bonnet, or the if the camera is not oriented properly, this method will fail . 

Another shortcoming is that the lanes are not properly blended in the video. 


### 3. Possible improvements with my pipeline

One potential improvement would be to use moving average techniques to blend the images properly in the video. 
Another improvement would be to somehow check if region of interest is chosoen properly and change it in real time if it is not working properly.
