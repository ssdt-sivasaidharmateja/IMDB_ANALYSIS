# IMDB Movie Data Analysis

This repository contains Python code for analyzing and visualizing the IMDB Movie dataset. The dataset includes information about movies such as title, runtime, ratings, revenue, and more.

## Table of Contents
- [Dataset Description](#dataset-description)
- [Setup and Installation](#setup-and-installation)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
  - [Movies with Long Runtime](#movies-with-long-runtime)
  - [Year with Highest Average Voting](#year-with-highest-average-voting)
  - [Year with Highest Average Revenue](#year-with-highest-average-revenue)
  - [Average Rating by Director](#average-rating-by-director)
  - [Top 10 Lengthy Movies](#top-10-lengthy-movies)
  - [Movie Counts by Year](#movie-counts-by-year)

## Dataset Description
The dataset used for this analysis includes the following features:
- Title
- Year
- Runtime (Minutes)
- Votes
- Revenue (Millions)
- Rating
- Director

## Setup and Installation
1. Clone the repository and ensure you have Python installed.
2. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Place the dataset (`IMDB-Movie-Data.csv`) in the appropriate directory.

## Data Cleaning

### Missing Values
- Visualized and calculated the percentage of missing values.
- Removed rows containing missing values using:
  ```python
  data.dropna(how='any', inplace=True)
  ```

### Duplicate Values
- Checked for duplicate data using:
  ```python
  data.duplicated().any()
  ```

## Data Analysis

### Movies with Long Runtime
Displayed titles of movies with a runtime of 180 minutes or more:
```python
data[data['Runtime (Minutes)'] >= 180]['Title']
```

### Year with Highest Average Voting
Identified the year with the highest average voting:
```python
data.groupby('Year')['Votes'].mean().sort_values(ascending=False)
```
Visualized using a bar plot:
```python
sns.barplot(x='Year', y='Votes', data=data)
plt.title('Votes by Year')
plt.show()
```

### Year with Highest Average Revenue
Found the year with the highest average revenue:
```python
data.groupby('Year')['Revenue (Millions)'].mean().sort_values(ascending=False)
```
Visualized using:
```python
sns.barplot(x='Year', y='Revenue (Millions)', data=data)
plt.title('Revenue by Year')
```

### Average Rating by Director
Computed the average rating for each director:
```python
data.groupby('Director')['Rating'].mean().sort_values(ascending=False)
```

### Top 10 Lengthy Movies
Identified and visualized the top 10 movies with the longest runtime:
```python
top10_movies = data.sort_values(by='Runtime (Minutes)', ascending=False)[['Title', 'Runtime (Minutes)']].head(10)
sns.barplot(y='Title', x='Runtime (Minutes)', data=top10_movies)
plt.title('Top 10 Lengthy Movies')
```

### Movie Counts by Year
Calculated and visualized the number of movies released each year:
```python
data['Year'].value_counts()
sns.countplot(x='Year', data=data)
plt.title('Count of Movies by Year')
```

## Results Interpretation
- **Movies with Long Runtime:** Displayed titles of lengthy movies.
- **Highest Average Voting Year:** 2012 had the highest voting.
- **Highest Average Revenue Year:** Identified using the grouped data.
- **Top Directors:** Directors with the highest average ratings.
- **Top 10 Lengthy Movies:** Visualized using bar plots.
- **Movie Counts by Year:** Distribution of movie counts over years.
