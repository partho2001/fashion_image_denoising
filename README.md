# De-noising images using Autoencoders
Steps for doing the code
1. Retrieve the data
Once, we retrieve the data from tensorflow.keras.datasets, we need to rescale the values of pixel range from (0-255) to (0,1), and for such we will divide all the pixel values with 255.0 to normalize them. NOTE: As autoencoders are capable of unsupervised learning (without Labels) and this is what we wish to achieve through this article, we will ignore labels from the training and testing dataset for fashionMNIST.

2. Adding the Noise
The raw dataset doesn’t contain any noise in the images but for our task, we can only learn to denoise the images that have noise already in them. So for our case, let’s add some noise in our data.

Here we are working with greyscale images, that have only 1 channel but that channel is not mentioned as an additional dimension in the dataset, so for the purpose of adding noise, we need to add a dimension of value ‘1’, which corresponds to the greyscale channel for each image in the training and testing set.


#Visualising a sample image 
![image](https://user-images.githubusercontent.com/42618752/188330912-13aa049b-b5c9-4be1-ac8f-7ca9b40ee178.png)

3. Create a Convolutional Autoencoder network
we create this convolutional autoencoder network to learn the meaningful representation of these images their significantly important features. Through this understanding, we will be able to generate a denoised version of this dataset from the latent dimensional values of these images.

#Some more photo
![image](https://user-images.githubusercontent.com/42618752/188330862-cb8ed745-db64-4d94-935e-f69ad68d928c.png)

4. Training the Model and Testing it
As discussed above already, we don’t have labels for these images, but what we do have is original images and noisy images, we can train our model to understand the representation of original images from latent space created by noisy images. This will give us a trained decoder network to remove the noise from the noisy image’s latent representations and get clearer images.

#Training some image data
![image](https://user-images.githubusercontent.com/42618752/188330879-ab53c711-1002-49ec-a8d0-ce16087e01ad.png)

Training loss and validation loss, both seem to be almost exact which means there is no overfitting and also there is no significant decrease in both the losses for the last 4 epochs, which says that it has reached the almost optimal representation between the images.



![image](https://user-images.githubusercontent.com/42618752/188330884-080ebdcc-c40c-42db-b0cb-a6f0ad879992.png)

Visualizing the Effect of Denoising:

#Final image after removing the noise
![image](https://user-images.githubusercontent.com/42618752/188330940-c1d35bbd-6100-488a-ad1c-b83ac8018430.png)
