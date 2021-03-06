# Landscape Classification
<h3> Transfer Learning on Inception v3 model using TensorFlow </h3>

I had a dataset (130 instances per class) of 4 types of landscape: <b>Mountains, Beach, Forest, City</b>

The most suitable approach with such a small dataset is transfer learning. The model I used was <b>Inception v3</b>, which is trained on over 1M images from over 1000 classes. 

<h4><p align="center">Some training instances</p></h4>

<p align="center">
  <img width="200" height="200" src='https://github.com/olafplacha/Landscape-Classification/blob/master/img/image105.jpg'/>
  <img width="200" height="200" src='https://github.com/olafplacha/Landscape-Classification/blob/master/img/image6.jpg'/>
  <img width="200" height="200" src='https://github.com/olafplacha/Landscape-Classification/blob/master/img/image115.jpg'/>
  <img width="200" height="200" src='https://github.com/olafplacha/Landscape-Classification/blob/master/img/image2.jpg'/>
</p>


<hr>
For training I used retrain.py script (provided by TF). First it created bottleneck files with every image's cache in order to speed up training (only the last layer is not frozen, so a particular image always has the same output from the previous layers, regardless of the last layer. Therefore we compute these values once and save in .txt files). Next we have to specify a few hyperparameters (train-val-test ratio, training and validation batch sizes, learning rate, number of training steps) and a few directories (where to save final model, summaries for TensorBoard, where to get data from). You can find it in params.txt file. Then training is started. You can see how the loss was decreasing during training

<p align="center">
  <img src="https://github.com/olafplacha/Landscape-Classification/blob/master/img/loss.png"/>
</p>

A bit suprisingly train, validation and test accuracies were 100%, even without much hyperparameters tuning

<hr>
<p align="center"><b>Below you can see a few testing instances with classes probabilities</b></p>

<p align="center">
  <img width="370" height="240" src="https://github.com/olafplacha/Landscape-Classification/blob/master/img/test5.jpg"/><br/>
  <b>City 98.2%</b>
</p>

<p align="center">
  <img width="370" height="240" src="https://github.com/olafplacha/Landscape-Classification/blob/master/img/test2.jpeg"/><br/>
  <b>Beach 98.9%</b><br/>
</p>

<p align="center">
  <img width="370" height="240" src="https://github.com/olafplacha/Landscape-Classification/blob/master/img/test3.jpg"/><br/>
  <b>Forest 99.3%</b><br/>
</p>

<p align="center">
  <img width="370" height="240" src="https://github.com/olafplacha/Landscape-Classification/blob/master/img/test4.jpg"/><br/>
  <b>Mountains 99.1%</b><br/>
</p>
<hr>
In order to compare the obtained accuracy I created a logistic regression classifier in TensorFlow (a really simple model, <b>much</b> simpler than Inception v3) that got 78.84% test accuracy. 
<hr>
In conclusion problem with classifying 4 distinct landscapes is not that difficult and can be tackled well with DL techniques. You can find the code for the logistic regression classifier in <a href="https://github.com/olafplacha/Landscape-Classification/blob/master/logistic_clf.ipynb">logistic_clf.ipnb</a>
<hr>
If you want to know more details about the project visit this <a href="https://www.youtube.com/watch?v=Qv2QHPvYvwo">link</a>

