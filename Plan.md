## Plan


##### 11-03-2018
* Naive Bayes performs well when we have multiple classes and working with text classification. Advantage of Naive Bayes algorithms are:
* It is simple and if the conditional independence assumption actually holds, a Naive Bayes classifier will converge quicker than discriminative models like logistic regression, so you need less training data. And even if the NB assumption doesn’t hold.
* It requires less model training time
* The main difference between Naive Bayes(NB) and Random Forest (RF) are their model size. Naive Bayes model size is low and quite constant with respect to the data. The NB models cannot represent complex behavior so it won’t get into over fitting. On the other hand, Random Forest model size is very large and if not carefully built, it results to over fitting.
* So, When your data is dynamic and keeps changing. NB can adapt quickly to the changes and new data while using a RF you would have to rebuild the forest every time something changes.


* The advantages of support vector machines are:

    1. Effective in high dimensional spaces.
    2. Still effective in cases where number of dimensions is greater than the number of samples.
       Uses a subset of training points in the decision function (called support vectors), so it is also memory efficient.
    3. Versatile: different Kernel functions can be specified for the decision function. Common kernels are provided, but it is also              possible to specify custom kernels.

* The disadvantages of support vector machines include:

    1. If the number of features is much greater than the number of samples, avoid over-fitting in choosing Kernel functions and                  regularization term is crucial.
    2. SVMs do not directly provide probability estimates, these are calculated using an expensive five-fold cross-validation (see Scores        and probabilities, below).
    
    
#### SVC
 * The C parameter trades off misclassification of training examples against simplicity of the decision surface. A low C makes the decision surface smooth, while a high C aims at classifying all training examples correctly by giving the model freedom to select more samples as support vectors.


#### 14-03-2018
* Input : Images(RGB/BGR)(64 x 64), Video frames with lanes and cars passing on them.
* Dimensions of ht eimage = 720 x 1280 ( H x W)
* Extracting Features depend upon the Model that we use, different models could be used.
* SVMs are suggested by Udacitu.
* Spatial Bin
    * Get the Image
    * Resize the Image
    * Use the Function called Ravel to Concatenate . Flattening is also used. This reduces the Feature size, without losing information.
    * Recollect: In CNN we had filter that would provide Sequence or 1-d Snapshots that would be really useful.
    * We would be left with 3 - channel flatten output.
    * Take the image, color space, resizwe size and concatenate by Ravel (Lesson 16)
* Color Histogram
    * The signature of the pixel intensity is plotted.
    * We require the signature of the Car- image.
    * Create a array of the Histograms for each Colorspace.
* HOG
    * Start with the intensity of the of the Direction of the Gradient in each pixel and create a signature. 
    * https://www.learnopencv.com/histogram-of-oriented-gradients/
    * 
    
* Feature Extraction
    * This phase could be used to reduce the dimensionality by either using decisio Tree or PCA
    
##### Training The network
* SVC - parameters to tune :C ,Gamma, Kernel etc.
* Grid Search these values
* Accuracy
* Model.
###### Sliding Window:
    * Define X1,X2 and Y1,Y2
    * Define the size of the window
    * Resize, Extract Features, Predict and Classsify.
    * Define and run the Window with algoritm(Each Window)
    * cv2.Rectangle to draw the boxes
    
#### 15-03-2018
1. Number of windows
2. Size of the Window.
3. X1, X2, Y1, Y2 must be considered based on the size of the window.
4. Overlapping is a parameter that has to be tuned.

### skimage.hog()
1. The scikit-image hog() function takes in a single color channel or grayscaled image as input, as well as various parameters. These parameters include orientations, pixels_per_cell and cells_per_block.

2. The number of orientations is specified as an integer, and represents the number of orientation bins that the gradient information will be split up into in the histogram. Typical values are between 6 and 12 bins.

3. The pixels_per_cell parameter specifies the cell size over which each gradient histogram is computed. This paramater is passed as a 2-tuple so you could have different cell sizes in x and y, but cells are commonly chosen to be square.

4. The cells_per_block parameter is also passed as a 2-tuple, and specifies the local area over which the histogram counts in a given cell will be normalized. Block normalization is not necessarily required, but generally leads to a more robust feature set.

5. There is another optional power law or "gamma" normalization scheme set by the flag transform_sqrt. This type of normalization may help reduce the effects of shadows or other illumination variation, but will cause an error if your image contains negative values (because it's taking the square root of image values).
