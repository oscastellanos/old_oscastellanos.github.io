---
layout: post
title: Interactive Segmentation with Imperfect Input
excerpt: "Digital Image Processing Course: My group's final project."
tags: [tensorflow, python, opencv]
categories: [computer vision]
comments: true
pinned: true
---

## Motivation
This project would assist in workflows that require image segmentation. For example, a web application where a user can upload a picture, click on the object the user wants to copy, and the web application will automatically segment the object of interest from the background. Afterwards, the user would be able to copy or save the object of interest, without having to worry about altering the original image.

## Problem Definition

Input: An RGB image, user interaction (such as clicks) that roughly marks the object of interest.
 
Output: A smaller portion of the original image containing the area, or object, of interest. An image where values close to one are pixels belonging to the object marked by the user and zeros are anything other than the object.
 
Need training?: Yes, we will need to train a model in order to obtain the boundaries of a user’s object of interest.
 
More about the definition: A user should need few interactions with the image for the object of interest to be segmented reasonably.


## Data

Each image has an annotation file giving a bounding box and object class label for each object in one of the twenty classes present in the image.
Data size and format: 2GB tar file
Ground truth format: Consists of a matrix mapping pixel locations to class type. The classes are:
1=aeroplane, 2=bicycle, 3=bird, 4=boat, 5=bottle, 6=bus, 7=car , 8=cat, 9=chair, 10=cow,
11=diningtable, 12=dog, 13=horse, 14=motorbike, 15=person, 16=potted plant, 17=sheep,18=sofa, 19=train, 20=tv/monitor
<br>
 
<a href="http://host.robots.ox.ac.uk/pascal/VOC/voc2012/index.html#devkit"> `Download link for public data` </a>
<br>
Evaluation data: 
GrabCut - 50 images
BSDS - 96 images

## Methodology
We’ll be creating a variation of a fully-convolutional encoder-decoder network. The network will be implemented in TensorFlow using Python.  We will also be creating initial concepts on Google’s Colab notebook environment.

## Experiment and Evaluation Metric
We will be using metrics from “Interactive Boundary Prediction for Object Selection”
Intersection over Union (IU): This is a region-based metric which measures the intersection over the union between a predicted segmentation mask and the corresponding ground-truth.
Boundary-Based F-score: Used to evaluate the quality of the boundaries produced.

## Expected Results
We expect to obtain a reasonably well performing network that will obtain the boundary of the object of interest. If there’s enough time, we will deploy the model in a functioning web application that allows a user to upload an image, select an object of interest, and return the boundary and image of the object of interest.
## Possible Difficulties
* We may not be able to accomplish everything we’ve set out to do, due to time constraints
* The loss function consists of multiple components and is difficult to understanding thoroughly. 
* GrabCut is implemented in MatLab, which may pose unforeseen challenges in terms of replicating it.
## Notices

The group members include Osvaldo Castellanos, Adolfo Gonzalez III, and David Parra.
<br>
This project is for the UTRGV Course CS 6367 Digital Image Processing, 2019 Spring. It is taught by <a href="https://faculty.utrgv.edu/hongkai.yu/index.html">`Dr. Hongkai Yu`</a>.
{: .notice}
