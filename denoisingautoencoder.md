---
title: 
layout: default
---

*previous* - [a neural nets overview](../index.html)
# denoising autoencoders

An autoencoder is a neural network used for dimensionality reduction; that is, for feature selection and extraction. Autoencoders with more hidden layers than inputs run the risk of learning the [identity function](https://en.wikipedia.org/wiki/Identity_function) -- where the output simple equals the input -- thereby becoming useless. 

Denoising autoencoders are an extension of the basic autoencoder, and represent a stochastic version of the autoencoder. Denoising autoencoders attempt to address identity-function risk by randomly corrupting input (i.e. introducing noise) that the autoencoder must then reconstruct, or denoise. 

### parameters/corruption level 

The amount of noise to apply to the input takes the form of a percentage. Typically, 30 percent, or 0.3, is fine, but if you have very little data, you may want to consider adding more.

### input/initiating a denoising autoencoder

Setting up a single-thread denoising autoencoder is easy. 

To create the machine, you simply instantiate an object of the class [DenoisingAutoEncoder](../doc/org/deeplearning4j/da/DenoisingAutoEncoder.html).

<script src="http://gist-it.appspot.com/https://github.com/agibsonccc/java-deeplearning/blob/master/deeplearning4j-examples/src/main/java/org/deeplearning4j/example/mnist/DenoisingAutoEncoderMnistExample.java?slice=18:22"></script>

That's how you set up a denoising autoencoder with one visible layer and one hidden layer.

Next, create a training set for the machine. For the sake of visual brevity, a toy, two-dimensional data set is included in the code below. (With large-scale projects, the training sets are clearly much more substantial.)

<script src="http://gist-it.appspot.com/https://github.com/agibsonccc/java-deeplearning/blob/master/deeplearning4j-examples/src/main/java/org/deeplearning4j/example/mnist/DenoisingAutoEncoderMnistExample.java?slice=23:31"></script>

This will train the specified denoising autoencoder with a corruption level of 0.3 and a learning rate of 0.1 on the x matrix in the dataset.

You can test your input with this snippet:

<script src="http://gist-it.appspot.com/https://github.com/agibsonccc/java-deeplearning/blob/master/deeplearning4j-examples/src/main/java/org/deeplearning4j/example/mnist/DenoisingAutoEncoderMnistExample.java?slice=44:65"></script>

If you see percentages rather than zeros, that's a good indicator your autoencoder is learning the structure of the data.

Next, we'll show you how to implement a [stacked denoising autoencoder](../stackeddenoisingautoencoder.html), which is simply many DAs strung together.