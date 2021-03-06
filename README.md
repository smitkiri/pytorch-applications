# PyTorch Applications
---
This repository contains the datasets I worked on while learning PyTorch. The notebooks have deep learning implementations using pytorch along with a discription of the techniques used. The notebooks in this repository are the following:

#### 1. CIFAR10
This dataset contains 60,000 images from 10 classes split into 50,000 training images and 10,000 test images. The images are colored with 32x32 dimensions. The modelling involves training a convolutional neural network with cross-entropy loss and Adam optimizer. The results are as follows:

|          | Training Set | Test Set |
|----------|--------------|----------|
| Loss     | 0.2397       | 1.1309   |
| Accuracy | 93.75%       | 66.51%   |

#### 2. Sonar

This dataset is used to discriminate between sonar signals bounced off a metal cylinder and those bounced off a roughly cylindrical rock. Each sonar pattern is a set of 60 numbers in the range 0.0 to 1.0.  Each number represents the energy within a particular frequency band, integrated over a certain period of time.

For this binary classification problem, I first tried using Logistic Regression (Just a single Neuron with sigmoid activation). The results were as follows:

| Logistic Regression | Training Set | Test Set |
|----------|--------------|----------|
| Loss     | 0.1627       | 0.1579   |
| Accuracy | 80.14%       | 82.26%   |

Then, I tried using a simple feed-forward neural network with 2 hidden layers (with 64 and 16 neurons respectively) to see if I get better results. 

| Neural Network | Training Set | Test Set |
|----------|--------------|----------|
| Loss     | 0.1896       | 0.4643   |
| Accuracy | 100.00%      | 82.26%   |

The model most probably overfit, as we can see 100% accuracy on training set and only 82% accuracy on test set.

## PyTorch

PyTorch is a scientific computing package that is intended for two sets of audiences:
- A repacement for ```numpy``` to use the power of GPUs. ```torch.tensor``` is equivalant to ```numpy.array```
- A deep learning research platform which is equivalant to ```tensorflow``` or ```theano```

#### Common functions in torch
A quick look at some of the most commonly used `torch` functions:
- `torch.empty(3, 6)`: Creates an uninitialized matrix of dimensions 3x6. The initial values in this matrix would be whatever values are present at the allocated memory location.
- `torch.rand(3, 6)`: Creates a matrix of dimensions 3x6 and initializes it with random values.
- `torch.zeros(3, 6, dtype = torch.long)`: Creates a matrix of all zeros with data-type `torch.long`
- `torch.tensor(x)`: Will create a tensor from a list/array `x`
- `x.size()`: Will give the dimensions of a tensor `x`
- `x.item()`: Will give the value of a 1-element tensor`x`
- `x.numpy()`: Converts a tensor `x` to `numpy.array`

#### Automatic differentiation

The `autograd` package in PyTorch provides automatic differentiation for all operations on tensors. This makes it easy to perform backpropogation on neural networks. For a tensor, if we set the `.requires_grad` attribute as `True`, it starts to track all operations on the tensor. If we want to get the derivatives, we can just call the `.backward()` function. The gradients are accumulated into `.grad` attribute.

To prevent tracking the history, we can wrap our code in `with torch.no_grad():` block. This is useful when we want to evaluate our model so that the gradient history is not stored in model parameters.

## References
[Deep Learning with PyTorch: A 60 Minute Blitz](https://pytorch.org/tutorials/beginner/deep_learning_60min_blitz.html)