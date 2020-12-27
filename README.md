## Introduction
The final project #2 work of the **GTR team** with contributors: [@xuanrgn](https://github.com/xuanrgn) [@TemirlanKudabayev](https://github.com/TemirlanKudabayev) [@assquire](https://github.com/assquire) [@Batyrbek98](https://github.com/Batyrbek98) for CSS503 Advanced Programming Technologies.  Project was created **for educational purposes only.**


## Documentation

#### 1.Brute-Force Matching with ORB Descriptors

Here, we will see a simple example on how to match features between two images. In this case, I have a queryImage and a trainImage. We will try to find the queryImage in trainImage using feature matching.
(The images are [/res/set-2/scene.png](https://github.com/xuanrgn/distinctive-image/blob/main/res/set-2/scene.png "/res/set-2/scene.png") and [/res/set-2/object.png](https://github.com/xuanrgn/distinctive-image/blob/main/res/set-2/object.png "/res/set-2/object.png"))

We are using ORB descriptors to match features. So let's start with loading images, finding descriptors etc.

Next we create a BFMatcher object with distance measurement cv.NORM_HAMMING (since we are using ORB) and crossCheck is switched on for better results. Then we use Matcher.match() method to get the best matches in two images. We sort them in ascending order of their distances so that best matches (with low distance) come to front. Then we draw only first 15 matches (Just for sake of visibility. You can increase it as you like)


#####  What is this Matcher Object?
The result of matches = bf.match(des1,des2) line is a list of DMatch objects. This DMatch object has following attributes:

- DMatch.distance - Distance between descriptors. The lower, the better it is.
- DMatch.trainIdx - Index of the descriptor in train descriptors
- DMatch.queryIdx - Index of the descriptor in query descriptors
- DMatch.imgIdx - Index of the train image.

#### 2. Brute-Force Matching with SIFT Descriptors and Ratio Test


This time, we will use BFMatcher.knnMatch() to get k best matches. In this example, we will take k=2 so that we can apply ratio test explained by D.Lowe in his paper.

#### 3.FLANN based Matcher

FLANN stands for Fast Library for Approximate Nearest Neighbors. It contains a collection of algorithms optimized for fast nearest neighbor search in large datasets and for high dimensional features. It works faster than BFMatcher for large datasets. We will see the second example with FLANN based matcher.

For FLANN based matcher, we need to pass two dictionaries which specify the algorithm to be used, its related parameters etc. First one is IndexParams. For various algorithms, the information to be passed is explained in FLANN docs.
