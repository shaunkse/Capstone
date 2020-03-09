# Capstone Project: Predict West Nile Virus 

### Introduction

Airbnb, Inc. is an online marketplace for arranging or offering lodging, primarily homestays, or tourism experiences. The company does not own any of the real estate listings, nor does it host events; it acts as a broker, receiving commissions from each booking.

Before booking any accomodation with Air Bnb, customers will usually want to consider the price & location of the apartment, followed by reading some reviews that have been submitted by past customers who have had their staycation at. The reviews section may consist of many reviews which require customers to do multiple clicks to the next page to read other comments/reviews that are ordered chronogically. Depending on the interest and the number of compiled number of reviews, potential customers may find that the process of reading reviews very time consuming and they may have already had some specific topics/categories of reviews they are only interested to read into. Because of this time consuming process, potential customers may stay on the booking website so long, but fail to do a booking and check out as the reviews are hinding in their way of decision making. 

### Problem Statement 

To ease the process in reading reviews, by providing categories in the review section for customers to choose.


### About The Data

The data given publicly by airbnb (http://insideairbnb.com/get-the-data.html) consist of 5 main datasets, namely listing, calendar, reviews and neighbourhood over multiple countries all over the world. For this project, we are only interested in Singapore's dataset, and only looking into reviews, hence we are only using reviews.csv, a detailed Review Data for listings in Singapore.

##### What was provided?
The reviews dataset for Singapore, were only collected and publicised monthly from March 2019 to November 2019. 

These are the respective features in the datasets
| Features       | Descriptions                                                 |
|----------------|--------------------------------------------------------------|
| listing\_id    | Id of the apartment/host                                     |
| id             | Identification number for each record                        |
| date           | Date of the review submitted by the reviewer \[YYY\-MM\-DD\] |
| reviewer\_id   | Reviewer personal ID based on their registered account       |
| reviewer\_name | Name of the Reviewer                                         |
| comments       | Main Content of the review given for the apartment/host      |




### EDA, Cleaning and Pre-processing

##### General Approach: 

1) Using Regular Expression to retain only english words
2) Checking & Removing null inputs
3) Checking & Removing duplicates
4) Checking & Removing automated messages
5) Removing Stopwords, lower-casing
6) Lamatizing & Tokenizing, keeping only nouns 

##### Some Findings:
1) Presence of chinese words, automated messages in the dataset
2) Huge number of duplicates as the datasets are compiled cumulatively across months
3) Mean number of reviews in each listing is around 17-18 reviews
4) Max number of reviews is 294, min is 1
5) Total 6993 apartments 


### Modeling: To Determine Presence of WNV

##### General Approach: 

Topic modelling using LDA  (Latent Dirichlet Allocation)
- Prepare corpus and dictionary to input into the LDA model
- Number of topics are ran from 3 to 13, total of 11 LDA are generated 


##### Metrics Used to Validate Model:

Coherence Score
Top 3 coherence score on the assigned number of topics are then visuzlised using gensim to see how the weight and relevance of each token/words correlates to the allocated topics. 

##### Findings:

n=5 LDA model performed the best and was selected. 

| Model                    | ROC\-AUC Score |
| ------------------------ | -------------- |
| LDA, n=13                | 0\.523         |
| LDA, n=12                | 0\.543         |
| LDA, n=11                | 0\.541         |
| LDA, n=10                | 0\.541         |
| LDA, n=9                 | 0\.538         |
| LDA, n=8                 | 0\.541         |
| LDA, n=7                 | 0\.528         |
| LDA, n=6                 | 0\.552         |
| LDA, n=5                 | 0\.566         |
| LDA, n=4                 | 0\.555         |
| LDA, n=3                 | 0\.534         |


### Conclusion & Recommendations 

LDA helped to categorize 5 main topics, they are inferred to be 
1) Facilities
2) Accessibility
3) Apartment/Room Amenities
4) Hospitality/Experience
5) Value

For a case study with an apartment having 294 reviews, topic modelling helped to compile 294 lists of reviews, into 5 tabs for the 5 topics. Instead of having to click 34 clicks to the next page to read the reviews that are ordered chronologically, users can click on any of the 5 topics of interest to read specifically before making a booking. 

A list of 294 reviews, is grouped into the 5 topics that consist of 127,64,40,35 & 28 reviews respectively.  


   
