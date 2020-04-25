A Reddit Flair Detector web application to detect flairs of India subreddit posts using Machine Learning algorithms.
The application can be found live at https://reddit-detector.herokuapp.com/

Approach

Going through various literatures available for text processing and suitable machine learning algorithms for text classification,
I based my approach using which described various machine learning models like Naive-Bayes, 
Linear SVM and Logistic Regression for text classification with code snippets. Along with this, 
I tried other models like Random Forest and Multi-Layer Perceptron for the task. 
I have obtained test accuracies on various scenarios which can be found in the next section.

The approach taken for the task is as follows:

Collect 100 India subreddit data for each of the 12 flairs using praw module.
The data includes title, comments, body, url, author, score, id, time-created and number of comments.
For comments, only top level comments are considered in dataset and no sub-comments are present.
The title, comments and body are cleaned by removing bad symbols and stopwords using nltk.

Five types of features are considered for the the given task:
a) Title
b) Comments
c) Urls
d) Body
e) Combining Title, Comments and Urls as one feature.

The dataset is split into 70% train and 30% test data using train-test-split of scikit-learn.
The dataset is then converted into a Vector and TF-IDF form.

Then, the following ML algorithms (using scikit-learn libraries) are applied on the dataset:
a) Naive-Bayes
b) Linear Support Vector Machine
c) Logistic Regression
d) Random Forest
e) MLP

Training and Testing on the dataset showed the Random Forest showed the best testing accuracy of 77.97% when 
trained on the combination of Title + Comments + Url feature. The best model is saved and is used for prediction
of the flair from the URL of the post.

Results
Title as Feature
Machine Learning Algorithm	Test Accuracy
Naive Bayes	0.6011904762
Linear SVM	0.6220238095
Logistic Regression	0.6339285714
Random Forest	0.6160714286
MLP	0.4970238095

Body as Feature
Machine Learning Algorithm	Test Accuracy
Naive Bayes	0.2083333333
Linear SVM	0.2470238095
Logistic Regression	0.2619047619
Random Forest	0.2767857143
MLP	0.2113095238

URL as Feature
Machine Learning Algorithm	Test Accuracy
Naive Bayes	0.3005952381
Linear SVM	0.3898809524
Logistic Regression	0.3690476190
Random Forest	0.3005952381
MLP	0.3214285714

Comments as Feature
Machine Learning Algorithm	Test Accuracy
Naive Bayes	0.5357142857
Linear SVM	0.6190476190
Logistic Regression	0.6220238095
Random Forest	0.6011904762
MLP	0.4761904762

Title + Comments + URL as Feature
Machine Learning Algorithm	Test Accuracy
Naive Bayes	0.6190476190
Linear SVM	0.7529761905
Logistic Regression	0.7470238095
Random Forest	0.7797619048
MLP	0.4940476190

Intuition behind Combined Feature
The features independently showed a test accuracy near to 60% with the body feature giving the worst accuracies during the experiments.
Hence, it was excluded in the combined feature set.
