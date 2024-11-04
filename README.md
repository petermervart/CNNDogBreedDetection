# Dog breed classification using CNN

#### This README is not a full explanation of our work, for more in depth comments proceed to Jupyter Notebook file.

## Important links

Detailed explanation with visualizations in jupyter notebook: [Notebook](Zadanie_4.ipynb)

Stanford Dogs Dataset: [Dataset](https://www.kaggle.com/datasets/jessicali9530/stanford-dogs-dataset)

Wandb Report: [Report](https://api.wandb.ai/links/xmervart/9heuazdh)

Presentation: [Presentation](Presentation.pdf)

## Dataset
Our dataset consists of 20 580 images divided into 120 classes (breeds), so approximately 170 images per class. We used validation and test subsets with ratio 90:5:5.

#### Example of images from dataset

![image](https://github.com/vgg-fiit/assignment-4-petoo51/assets/55833503/c5d6f835-b9c8-4450-9913-0c918511a77f)

### Model
Our model consists of blocks that start with depthwise convolution, which is followed by batch normalization and activation function. This is then repeated but with normal convolution. These blocks are inspired by MobileNetV1. Every time the amount of filters is increased in block, we lower the size of images using strides to find more detailed features. We gradually increase the amount of filters in each block and then apply global average pooling that is directly connected to the final dense layer with 120 neurons and softmax activation used for classification.

## Training

#### Loss during training

![loss_graph](https://github.com/vgg-fiit/assignment-4-petoo51/assets/55833503/f9f13051-e584-4788-83b9-5958f3efa2a3)

#### Accuracy during training

![acc_graph](https://github.com/vgg-fiit/assignment-4-petoo51/assets/55833503/1b43f575-2817-49df-b436-e9659b37983f)

## Results

In the end we were able to achieve accuracy of 93.73 % on training subset, 93.33 % on validation subset and 92.38 % on test subset. Results show that our model is decently precise and is not overfitted on any of the subsets.

#### Problematic classes

We plotted the top 10 classes that have the most false positives and false negatives. We can see that the amount of false positives and false negatives in classes is about the same. This means we do not have a class that is an outlier in the sense of accuracy. When we examined the data we found out that some breeds look very similiar to each other. This is the case for most of these top faulty classes too.

![image](https://github.com/vgg-fiit/assignment-4-petoo51/assets/55833503/ee099208-1f1e-467c-be6f-82932f3fbaea)

