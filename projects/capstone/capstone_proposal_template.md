# Machine Learning Engineer Nanodegree
## Capstone Proposal

Allstate Claims Severity - Kaggle Contest

Siddartha Tondapu
December 06, 2017

### Domain Background

Automobile accidents are involuntary and are often expected. Nearly 1.3 million people in the world and 37,000 people in the United States alone lose their life in these tragic accidents. While these are major accidents, there are many minor accidents and fender benders that cause devastating psychological damages. During these times, the victim wants to focus more time on his family, friends, and loved ones than to deal with insurance claims. Unfortunately, I was involved in a small fender bender recently, and I felt the whole process of claiming for insurance to be long and tedious. With so many accidents happening every day, I realized there can be better ways to make the whole process quick and seamless.


### Problem Statement

Allstate, an insurance company, saw this as a bottleneck and decided to automate the whole process by predicting the cost and severity of the claim. Our goal in this project is to use machine learning algorithms to model the cost and severity of a claim. We have been given some input variables (both continuous and discrete/categorical). Using these input variables, we will be predicting the output cost of the claim by using a regression model. Since cost is a continuous value, we will use a piecewise function to define the severity. For example:
- cost of claim is < 1000 =  minor severity
- cost of claim > 1000 and < 5000 = medium severity
- cost of claim > 5000 = major severity

### Datasets and Inputs

Allstate has provided us with some test and training data. It can be found here: https://www.kaggle.com/c/allstate-claims-severity/data

There are two files: train.csv and test.csv.
Each row in the dataset is associated to a claim. The input labels names are hidden; however, we are provided with the type of the variable. There are 14 continuous variables and 116 categorical/discrete variables or columns associated to each row. Using these input fields, we are supposed to predict the target variable called loss. Loss variable is a continuous value is associated to the price of the claim. In the training dataset, the loss column is removed.

Finally, there are 188318 claims in training data and 125546 claims in testing data.


### Solution Statement

Since we are using 116 categorical and 14 continuous data points to predict a target value: loss (continuous), this is a prime candidate for supervised regression model. We need to reduce the number of input variables, convert categorical to discrete numbers, and finally use one of a well known regression model such as SVM, LinearRegression, Decision Trees, etc to predict the target variable. I will use GridSearch to fine tune the params for the model in sklearn.


### Benchmark Model

Kaggle provides average scores of previous submissions here: https://www.kaggle.com/c/allstate-claims-severity/leaderboard
I will download the data as a CSV, remove any scores thats greater than 5000, and find the mean/average scores. Upon doing this calculation, the mean score was 1222.24. This score is the mean absolute error and the goal is to reduce this number. The average score can be used as a benchmark model for our linear regression model.


### Evaluation Metrics

Our model will be evaluated on the mean absolute error (MAE) between the predicted loss and actual loss. This evaluation metric is provided to us by Kaggle. In general, our objective is to minimize the MAE.

We will use the claims or input variables from test.csv. Using our regression model, we will predict the loss or cost of a claim. Finally, we will subtract the predicted error from actual error, find absolute value, and find the mean of these numbers. This will be the MAE.


### Project Design

We will be using three steps:
- Data Exploration
In this step, we will investigate the data i.e. finding the mean, mode, median, and standard deviation. This will help us to identify any outliers and possibly remove them to avoid skewed results. We can remove any null values if they have negative impact on the outcome. Plot them to see if any two independent variables are related and use PCA to reduce the dimensionality of the data.

- Training the Datasets
We will split the data into two sections: Testing and Training. We will then use multiple supervised learning algorithms like: Linear Regression, SVM, Decision Trees, etc to find the best algorithm. Finally, we will use sklearn's grid search to find the best params that optimize our results.

- Testing and Optimizing
Finally, we will use our model to predict the target variables from test.csv. These results can be uploaded on Kaggle to measure our accuracy using mean absolute error described above.
-----------

### Citations
- https://www.kaggle.com/c/allstate-claims-severity
- http://asirt.org/initiatives/informing-road-users/road-safety-facts/road-crash-statistics
- http://scikit-learn.org/stable/supervised_learning.html
- https://en.wikipedia.org/wiki/Mean_absolute_error
