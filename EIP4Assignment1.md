

#                          EIP2:Assignment-1



### Convolution:

*Convolution* in mathematics means:"A function that is derived by the integration of given functions".

The convolution expresses how the shape of one is modified by the other.



The analogy  of *Convolution* is similar in case of image processing  or CNN as well.In case of CNN,we apply convolution to input data (which is whole of the image) using a *convolution filter* which is something like a patch which is traversing across the image

The diagram below explains *Convolution.*Consider the input image as the Blue Box and the *Convolution filter* as the green box

![](C:\Users\sudreddy\Downloads\1_cTEp-IvCCUYPTT0QpE3Gjg@2x.png)



The result of multiplication of  3*3 values of *Convolution Filter*  to the  first 3*3 the input image is what *Convolution* means . As shown below

![](https://cdn-images-1.medium.com/max/1200/1*cTEp-IvCCUYPTT0QpE3Gjg@2x.png)

The output of the convolution is one single value which would be sum of all the multiplications shown in the figure .Each time the Convolution filter traverses across the image it generates  a value which is nothing but summing up the multiplication of 3 * 3  values of *Convolution Filter* with 3*3 values of  input image.

For the diagram about since 3*3 traversals are possible, it will generate altogether 3 * 3 values after convolution.The first of the value which is the output of the summing of the multiplication of the figure above  would be   1*1  + 1 * 0 + 1* 1  +  0*  0 + 1 * 1 + 1 * 0 + 0 * 1 +  0 * 0 + 1* 1 = 4

The same is depicted in the figure below.Note similar operation can be performed to get the value of each cell(which is nothing but  output of  convolution  of each traversal done by the *Convolution filter*).



![](https://cdn-images-1.medium.com/max/1200/1*ghaknijNGolaA3DpjvDxfQ@2x.png)



### Filters/Kernels:

Filters or Kernels in the world of Computer vision  are the feature extractors .We can have multiple features of a image e.g gradient,edge,colour,texture etc.

We can use  kernel for each of the feature e.g: We would use the 1st Kernel for extracting edges,the 2nd one for extracting gradients,the third for extracting texture and so on...

The below example show how different features e.g Identity, EdgeDetection, Sharpen are extracted out of the image.

![](https://ujwlkarn.files.wordpress.com/2016/08/screen-shot-2016-08-05-at-11-03-00-pm.png)

Consider kernel(feature extractor) as detecting edges.The Edge Detector Kernel when traverse over the image  would generate the output something like below.



![](https://www.owlnet.rice.edu/~elec539/Projects97/morphjrks/kfig2.jpg)





We can also think of having separate kernel each for one types of edges e.g Vertical Edge kernel and Horizontal Edge kernel

The way the kernels extract features is by convoluting over the  image.Each time a Kernel convolute over the image it  would generate a feature 

The various Kernel sizes used for image processing considering the CPU/GPU limitations of the convolution operation is 3 * 3  or 1*1.  





### Epoch:

*Epoch* in the context of Neural Networking is one round of learning  of the complete data set(usually all of the training dataset)  by the Neural Network.This learning includes both forward pass and backward pass of all the training examples over the Neural Network layers.



In case of  Convolutional Neural Networks(CNN) an epoch would be  reading the image and generating various layers of features as depicted below:

The steps shown below is one epoch for a CNN.We need to repeat the same steps multiple times i.e multiple epochs to achieve the desired accuracy.

![](https://cdn-images-1.medium.com/max/1600/1*VqRKWmxwIakOSnWPURoCSA.jpeg)



Each epoch would be run with different set of weights and biases and will have different learning rate.The idea of  running multiple epochs with different sets of weights and biases for a Neural Networks  is to achieve the desired output(closed to the actual results which is actual image in case of a computer vision problem ) without any under fitting or over fitting.  

  



### 1*1 Convolution:

When we use filter/kernel size 1 for convoluting  over a image we call it as  1 * 1 *Convolution*

The usual convolution use for a CNN which would give optimal results is 3 * 3.

The idea to go with 1*1 convolution with the recent advancement in CNN is to make image processing less compute intensive especially over the 3D space i.e while convoluting through multiple feature maps

Consider  the example below:

In case we go with 5 * 5 * 3 filter,we are performing  5* 5 * 3  matrix multiplication at a particular location of filter and in case we need to traverse over the complete 32* 32 * 3 we would be performing  these  5*  *5 * 3 multiplications 32 * 32 times  and considering  a stack of 10 feature maps we need to repeat the operation 10 times (i.e together we are performing 5 *5 *3 multiplications 32 * 32 * 10 times  )   

![](https://cdn-images-1.medium.com/max/1200/1*BSLjlJf31gj98ABJMCt3-g@2x.png)

In a usual CNN there would be 64,128,512 feature maps hence the amount of computation of 5 *5 * 3  multiplications increases exponentially  to 32 * 32 *512 which is huge. Same issue with 3 * 3 convolution filter as well as we would be performing 3* 3* 3 computations  32 * 32 *512 times. In order to reduce the computation we usually go with 1 * 1 convolutional filter which in this case means  1 * 1 *3 matrix multiplications  instead of  3 *3 *3 or 5 * 5 * 3.



### 3*3 Convolution:

When the Kernel size convoluting over a image is  3*3  ,its considered as  3  * 3  *Convolution*

We typically go with 3 * 3 convolution and not  5 * 5 or 7 *7 or 11 * 11.The idea of going with 3 * 3  is its less compute intensive as there are a total of 9 multiplications at a particular point of time  as compared to 25,49,121 multiplications in   5 * 5 , 7* 7 , 11 * 11 respectively.

The diagram below  shows a 3*3 Convolution over a 5 *  5 image.Each time a 3 * 3 Kernel convolves over the image it reduces the size of the image by 2.For example in the case below,when a 3*3  kernel is run over a   5 * 5 image,the output feature Map generated would be 3*3



![](https://icecreamlabs.com/wp-content/uploads/2018/08/33-con.gif)



Similarly a 7 * 7 image would be reduced to 5 * 5,11*11 would be reduced to 9 * 9.

200*200 would be reduced to 198 *198 .

In case we want to go with 5 * 5 convolution we can combine two 3 * 3.In case we want to go with 7 * 7 we can combine 3 3 * 3  and so on....   





### Feature Maps:



A feature map is the output generated  out of kernel convolution  over the image.As shown in the figure below each time the kernel slides over the image,  3*3 matrix multiplication happens which generates a single output(which is the summation of all 3 * 3 matrix multiplication).Since there are 9 slides possible for a  3*3 kernel over 5 *5 image a total of  9 outputs would be generated which is nothing but the *Feature Map*  



![](https://cdn-images-1.medium.com/max/1200/1*VVvdh-BUKFh2pwDD0kPeRA@2x.gif)

Feature Maps are also known as *Channels*.For example a Kernel extracting edges when convolve over an image would generate a Channel/Feature Map of edges

A gradient Kernel convolution would result in Feature Map of gradients.

Similarly, a texture Kernel would generate a Feature Map of textures and so on 

Edge,gradient,texture could be first layer of feature Maps .More complex feature Maps  can be derived out of the first layer of feature Maps e.g we can combine edges and gradients to get arcs as feature Maps in the second layer  of CNN and multiple  feature Maps of arcs  can be combined to form an *Eye* in the third layer of CNN and so on.. 



The below diagram shows feature Maps at various CNN layers.



### ![](https://cdn-images-1.medium.com/max/1200/1*OHifHVQLIIumP865ASipXA.png)





### Feature Engineering (older computer vision concept):



Several attempts were made by the researchers  during the initial days in the field of  image processing and computer vision.Various algorithms were developed in this area and a comparative study was made to access this algorithms based on areas e.g  speed,sensitivity,occlusion and others.

The algorithms and their respective images were mainly categorized into two groups:feature based and texture based.

Under this two groups the following most widely used algorithms are accessed:

 1)*Colour Histogram:*

This was the first attempt toward image processing.While color histogram was  fast in finding out **color distribution features** in a given image hence good for the basic requirements.It was not good in matching large set of images in  Consistency and Accuracy.

2)*FAST(Features from Accelerated Segment Test):*

Later point of time image recognition was done through **identification of corners and edges**.Termed as **"Harris Detector"** This was only detecting corners and had difficulty in obtaining major level descriptors e.g surfaces and objects.A new corner detector algorithm was coined after a decade named as FAST(Features from Accelerated Segment Test)



3)*SIFT (Scale Invariant Feature Transform):*

The feature based detectors could able to perform well when objects have same colour or identifiable corner or edge.

They don't perform well in case there is a variation in colour distribution,scale,illumination,rotation or affine transform.

To overcome this David Lowe came with SIFT (Scale Invariant Feature Transform) to extract features that can vary in scale,rotation,illumination etc.These algorithms are **Textured-Based algorithms**

![](https://ars.els-cdn.com/content/image/1-s2.0-S1110866513000248-gr2.jpg)





### How to create an account on GitHub and upload a sample project:

1.Go to http://www.github.com and click on "Step1:Create Personal Account"



![](https://www.wikihow.com/images/thumb/2/2c/Join-github-1.jpg/728px-Join-github-1.jpg)



2.Add all the details and click on Create Account

![](https://www.wikihow.com/images/thumb/5/52/Join-github-2.jpg/541px-Join-github-2.jpg)

3.Fill in the details as mentioned below to create the Organization

![](https://developers.sap.com/tutorials/webide-github-creating-org/_jcr_content.github-proxy.1538079938.file/p1_4.png)



4.Skip Step3 i.e Invite Organization Members as its an optional step





5.Install Git on Windows and run the following command to set up git.

Note the user.name and user.email needs to be replaced by what you have given while account creation





```
git config --global user.name 'My_Name'
git config --global user.email 'myEmail@wherever.com'
git config --global color.ui 'auto'
```



6. Create a directory under C drive and run  Git Bash there:



![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Bash-Here-Git-Tutorial-Edureka.png)





7.Run git init to create an empty Git repository.It will create a .git directory along with subdirectories and template files



![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Initialize-Git-Tutorial-Edureka.png)







> 8.Add files e.g  edureka1.txt,edureka2.txt,edureka3.txt,edureka4.text to the directory by running **git add -A.**



![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Add-All-Git-Tutorial-Edureka.png)



9. run **git commit -m "some meaningfull message"** to commit the files to the local repository

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Commit-Git-Tutorial-Edureka.png)



10.Run **git pu origin master** command.This command will copy files from master branch available at the remote repository to the local repository

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Pull-Origin-Master-Git-Tutorial-Edureka.png)



In order to publish you local changes to the central repository run the following command:



![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Local-Repository-Files-Before-Push-Git-Tutorial-Edureka-2.png)





![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Push-Origin-Master-Git-Tutorial-Edureka.png)





![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/GitHub-after-Git-Push-Git-Tutorial-Edureka.png)

