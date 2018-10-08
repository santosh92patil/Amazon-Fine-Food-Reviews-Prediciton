# CS1-Amazon-Fine-Food-Reviews-Prediciton
**Checking predictions results for all ML models based on Amazon Fine Food Reviews Dataset.** 

#### Objective: Given a review we need to classify whether it is positve or negative.(Predicting semantics of the review)

##### Data Description:

Taken dataset from kaggle platform (link :https://www.kaggle.com/snap/amazon-fine-food-reviews).

The Amazon Fine Food Reviews dataset consists of reviews of fine foods from Amazon.

- Number of reviews: 568,454
- Number of users: 256,059
- Number of products: 74,258
- Timespan: Oct 1999 - Oct 2012
- Number of Attributes/Columns in data: 10

Attribute Information: Columns in the dataset

1. Id
2. ProductId - unique identifier for the product
3. UserId - unqiue identifier for the user
4. ProfileName
5. HelpfulnessNumerator - number of users who found the review helpful
6. HelpfulnessDenominator - number of users who indicated whether they found the review helpful or not
7. Score - rating between 1 and 5
8. Time - timestamp for the review
9. Summary - brief summary of the review
10. Text - text of the review

#### Data Preprocessing
Note:
>These steps are same for every model

In *Data Preprocessing* we check whether there are any **duplicate values, missing values** and we deal with them initally. In the Dataset I have found and removed them. As we see from the attribute information, *Value of HelpfulnessDenominator should be always greater than value of HelpfulnessNumerator*, because HelpfulnessDenominator is the sum of both useful review and not useful review while HelpfulnessNumerator is only the number of users who found the review helpful. So removing records or datapoints that doesnt satisfy this condition.

we are also removing the neutral reviews(3 star reviews) from the dataset for better predicitons, considering 1 & 2 star reviews as negative reviews and 4 % 5 star as positive reviews.

**Text Preprocessing: Stemming, Stop-words removal, HTML tags removal, Punctuation marks removal**

Now that we have finished deduplication our data requires some preprocessing before we go on further with analysis and making the prediction model.

Hence in the Preprocessing phase we do the following in the order below:-

1. Begin by removing the html tags
2. Remove any punctuations or limited set of special characters like , or . or # etc.
3. Check if the word is made up of english letters and is not alpha-numeric
4. Check to see if the length of the word is greater than 2 (as it was researched that there is no adjective in 2-letters)
5. Convert the word to lowercase
6. Remove Stopwords
7. Finally Snowball Stemming the word (it was obsereved to be better than Porter Stemming)
8. After which we collect the words used to describe positive and negative reviews

**Converting Text into Numerical vectors**

For this step, you can check my kaggle kernel(link: https://www.kaggle.com/shashanksai/text-preprocessing-using-python) where I have explained detailly how to convert words into vectors so that algorithm can read them.
we have four major vectorizers to convert text ot vectors
- Bag of Words
- Term Frequency Inverse Document Frequency (TF-IDF)
- Average Word2Vec
- TF_IDF Word2Vec
(*You can also find the optimal codes*)
