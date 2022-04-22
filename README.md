# NYC Airbnb: Price Prediction with Machine Learning

## Soo Ho (John) Park

# Introduction

New York City is a financial powerhouse, multicultural hub, and tourist hotspot, being one of the most coveted real estate areas in the world. The stakeholders are current and prospective Airbnb hosts who are seeking real estate investments opportunities in New York City. With countless features and variations involved in Airbnb listings, it is exceedingly difficult to understand which features are important in influencing price. Thus, I aim to answer the following question: what home features and characteristics predict a higher range of prices?

By utilizing multiple machine learning models as a predictive measure, I offer a set of recommendations tailored to the airbnb hosts' needs. I analyze which indicators can predict the price per night of a listing and find which type of homes hosts ought to invest in. Through thorough data analysis, I discovered that our stakeholders ought to prioritize privacy, credibility, and flexibility to ensure a higher range in price. I recommend that Airbnb hosts seek out Entire Homes, Apartments, or Private rooms as opposed to shared rooms, since privacy plays a huge role in influencing price. Furthermore, number of reviews and high review scores influence price, meaning that users are seeking for credible and low risk places that have already been verified by others. Hosts ought to ensure that their listings have multiple high ratings reviews. Lastly, flexible policies that allow users to have more availability and shorter minimum nights can influence price as well.

![Airbnb-NYC-law.jpg](attachment:Airbnb-NYC-law.jpg)

# Data Understanding

The original data set `listings.csv` was extracted from a website called Inside Airbnb, which is an independent, non-commercial, open source data tool that synthesizes Airbnb data. This dataset contained 38277 entries with 74 columns, consisting of listings in the New York City area. The relevant features included price per night, longitude, latitude, room type, neighborhood, number of reviews, review score rating, and etc. From a business understanding standpoint, such features of the listings, specifically those based on type of room, location, and users' reception, seemed to have a influence on price. Thus, analyzing the relationship between such features and price, I sought out to create a model that accurately predicts price per night. One feature that could have been more helpful in gaining perspective on price selections would be occupancy rate, which was not made public. How many days the listings were occupied could have influenced price as well, considering supply and demand affects pricing.

# Data Preparation

This project used a variety of Python libraries to carry-out this project. 
Pandas  v1.1.3
Numpy   v1.18.5
SciKit-Learn  v0.23.2
Matplotlib v3.3.1
Folium

### Data Cleaning:

Starting data preparation, I first removed the irrelevant features, since 74 features were far too extensive. I then converted the price per night from string to float, separated the listings into two price ranges as categorical variables, and removed outliers that are 3 standard deviations away.

For data visualization, I created a map of New York City that displays all listings with yellow circles representing higher priced listings and green circles representing lower priced listings.

### Feature Engineering:

By using one hot encoding, I binned neighborhood_group_cleansed and type of room into dummies to observe if location and room type had an influence on price. For room type, the dummies consisted of Entire home/apt, Hotel room, Private room, and Shared Room. For neighborhoods, the dummies consisted of Manhattan, Queens, Brooklyn, Bronx, and Staten Island.


### Map

For data visualization, I extracted the `latitude`,`longitude`,and `price` into a separate dataframe, and then used folium to map out listings.



### Words Associated with High Prices

By using the wordcloud technique on `description`, I explored which specific words often used to describe listings with high prices.


# visualize distribution of price (target variable)



### Neighborhood

Since location, specifically neighborhoods, may have a strong influence over the price per night of listings, I first visualized the distribution of listings by neighborhood

df.neighbourhood_group_cleansed.value_counts()

df2

df.neighbourhood_cleansed.value_counts()

df.describe()

plt.figure(figsize=(8, 4))
df.neighbourhood_group_cleansed.value_counts().plot(kind='bar', color='b')
plt.xticks(rotation=90)
plt.ylabel('count')
plt.xlabel('neighborhood')
plt.show()

df.neighbourhood_cleansed.value_counts()

# Final Model
## Evaluation Metrics
![Confusion Matrix of Final Model](photos/evalmetrics_finalmodel.png)

Mean accuracy of the final model: 0.773489765351972

Precision Score of the final model: 0.7716570413149711

AUC of the ROC Curve of the final model: 0.85

![ROC-AUC of Final Model](photos/ROCAUC_finalmodel.png)

### Model Evaluation


### Logistic Regression Model



# Best Feature

What are the most important features for predicting the price range of a listing? I utilized the ExtraTreesClassifier method. This class implements a meta estimator that fits a number of randomized decision trees (a.k.a. extra-trees) on various sub-samples of the dataset and uses averaging to improve the predictive accuracy and control over-fitting.


# Conclusion

I recommend that Airbnb hosts seek out Entire Homes, Apartments, or Private rooms as opposed to shared rooms, since privacy plays a huge role in influencing price. Furthermore, number of reviews and high review scores influence price, meaning that users are seeking for credible and low risk places that have already been verified by others. Hosts ought to ensure that their listings have multiple high ratings reviews. Lastly, flexible policies that allow users to have more availability and shorter minimum nights can influence price as well.

For future steps, I aim to discover if geolocation to cafes, restaurants, and green space has a heavy influence on price. Moreover, what words are used to describe the listing may have an impact on price as well, since rhetoric and flowery language can catch users’ attention. I would also like to understand which specific advertising tactics can lead to higher prices.
