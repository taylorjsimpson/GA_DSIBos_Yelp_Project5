# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Estimating Affluence With Yelp Data

## Project Authors
[Colleen Kenney](https://github.com/cobkenney) | [Jerel Novick](https://github.com/JerelNovick) | [Taylor Simpson](https://github.com/taylorjsimpson) |

## Contents of Repo

<!--ts-->
* [Code](https://git.generalassemb.ly/cobkenney/Project_5/tree/master/code)
  * [Data Collection & Data Aggregation](https://git.generalassemb.ly/cobkenney/Project_5/blob/master/code/Data_Collection_%26_Aggregration.ipynb)
  * [Exploratory Data Analysis](https://git.generalassemb.ly/cobkenney/Project_5/blob/master/code/Exploratory_Data_Analysis.ipynb)
  * [Initial Supervised Learning Model](https://git.generalassemb.ly/cobkenney/Project_5/blob/master/code/Initial_Supervised_Learning_Modeling.ipynb)
  * [Additional Supervised Learning Model](https://git.generalassemb.ly/cobkenney/Project_5/blob/master/code/Additional_Supervised_Learning_Modeling.ipynb)
  * [Unsupervised Learning Model](https://git.generalassemb.ly/cobkenney/Project_5/blob/master/code/Unsupervised_Learning_Modeling.ipynb)
* [Data](https://git.generalassemb.ly/cobkenney/Project_5/tree/master/data)
<!--te-->

## Table Of Contents
[1. Problem Statement](#1.-Problem-Statement)<br>
[2. Executive Summary](#2.-Tools-&-Methodology)<br>
[3. Data Dictionary](#3.-Data-Dictionary)<br>
[4. Key Takeways](#4.-Key-Takeaways)<br>
[5. Next Steps](#5.-Next-Steps)<br>

## 1. Problem Statement

[New Light Technologies](https://newlighttechnologies.com/) tasked us with estimating the affluence of a neighborhood based on the Yelp designated one to four dollar sign scale for businesses and services in a given city. While traditional methods typically estimate wealth of a locality based on demographic characteristics (e.g. income or unemployment rate), the novelty of this approach is in its use of big data related to commercial activity and cost of product and services as an indicator for affluency.

Null Hypothesis: Yelp pricepoints do not predict affluence of an area.

## 2. Executive Summary

Data was gathered from Yelp for the most populous city in each of the 50 states. The data was categorically divided into restaurants, hotels, shopping, nightlife and beauty, which totaled almost 85,000 datapoints.  The datapoints were then aggreated for each of the cities based on Yelp's price ratings ($$$, $$$, $$, $) and number of stars (1 to 5). Affluency was measured by the median household income in each of the cities. This data was retrieved from City-Data.com.

Using the Yelp data, supervised and unsupervised learning models were built to predict affluency or identify patterns in the data.

The decision was made to also build an alternate model using select socio-economic metrics, which were completed level of education of a city's residents, population density, land area, property crime rate, and violent crime rate. 

The following packages were imported to conduct this analysis.

|                |            |         |         |            |          |
|----------------|------------|---------|---------|------------|----------|
| Pandas         | Matplotlib | Seaborn | Sklearn | Numpy      | Requests |
| Beautiful Soup | YelpAPI   | Regex   | Plotly  | Statsmodel | Scipy    |


## 3. Data Dictionary

Sources:
* [Yelp API](https://www.yelp.com/fusion)
* [American Factfinder - Census](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml)
* [Population Density](https://www.governing.com/gov-data/population-density-land-area-cities-map.html)
* [FBI Crime](https://ucr.fbi.gov/crime-in-the-u.s/2017/crime-in-the-u.s.-2017/topic-pages/tables/table-4)
* [Zillow](https://www.zillow.com/research/data/)

|Feature|Type|Description|
|---|---|---|
|**abbrev_state**|*object*|The state abbreviation for the city|
|**city**|*object*|The US city that corresponds|
|**average_rating_x_dollar**|*int*|The average rating for a given dollar $ category (x)|
|**average_review_count_x_dollar**|*int*|The average review coutn for a given $ category(x)|
|**one_dollar**|*int*|The number of businesses in the $ category for a given city|
|**two_dollar**|*int*|The number of businesses in the $$ category for a given city|
|**three_dollar**|*int*|The number of businesses in the $$$ category for a given city|
|**four_dollar**|*int*|The number of businesses in the $$$$ category for a given city|
|**city_median_household_income**|*int*| he median household income for a given city in $|
|**weighted_x_dollar**|*int*|The number of businesses in a category times the number of $s|
|**total_businesses**|*int*|The total number of businesses retreived for each city|
|**bachelors_or_higher**|*float*|The % of population who has a bachelors or higher|
|**high_school_or_higher**|*float*|The % of population who has a high school degree or higher|
|**home_index**|*int*|Zillow's smoothed, seasonally adjusted measure of the median estimated home value across a given region and housing type. It is a dollar-denominated alternative to repeat-sales indices.|
|**2016_population**|*int*|2016 population of the city|
|**land_area**|*float*|Square miles of city|
|**population_density**|*int*|Person per square miles|
|**property_crime_per_100k**|*int*|# of property crime occurences per 100,000 people|
|**violent_crime_per_100k**|*int*|# of violent crime occurences per 100,000 people|

## 4. Key Takeaways

The linear regression models that were created were extremely overfit and not very predictive. They were not indicitave of statistically significant relationships due to high p-values and coefficients without a cohesive trend. This has been attributed to the small number of observations and features used in the model. When we added other predictors of affluence, the models did improve, but they still were not strong models because we had limited data after we aggregated the yelp data. Overall, we failed to reject our null hypothesis for the supervised learning models. For the unsupervised learning model, there did seem to be some identifiable patterns. They were not the strongest of patterns, but they did exist.

## 5. Next Steps

Further work should be done with a more extensive set of observations (cities). Our biggest limitation by far was the number of observations after aggregating the data. The Yelp API also proved to be difficult to use because inputting location criteria does not gaurantee results in that location. Additionally, a richer and more diverse set of features could be used, such as percentage increase in population of a city within the last 10 years and average number of tourist dollars spent in the city per year. Experimentation should also be done with other measures of affluency, such as market capitilization of biggest employers in the city, metropolitan area transit stations, and number of Professional Sports Teams.    
