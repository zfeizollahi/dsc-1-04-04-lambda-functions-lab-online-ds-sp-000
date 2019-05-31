
# Lambda Functions - Lab

## Introduction|

In this lab, you'll get some hands on practice creating and using lambda functions.

## Objectives
You will be able to:
* Understand what lambda functions are and why they are useful
* Use lambda functions to transform data within lists and DataFrames

## Lambda Functions


```python
import pandas as pd
df = pd.read_csv('Yelp_Reviews.csv')
df.head(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
    </tr>
  </tbody>
</table>
</div>



# Simple Arithmetic

Use a lambda function to create a new column called 'stars_squared' by squarring the stars column.


```python
#Your code here
df['stars_squared'] = df['stars'].apply(lambda x: x**2)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Ums3gaP2qM3W1XcA5r6SsQ</td>
      <td>0</td>
      <td>2014-09-05</td>
      <td>0</td>
      <td>jsDu6QEJHbwP2Blom1PLCA</td>
      <td>5</td>
      <td>Delicious healthy food. The steak is amazing. ...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>vgfcTvK81oD4r50NMjU2Ag</td>
      <td>0</td>
      <td>2011-02-25</td>
      <td>0</td>
      <td>pfavA0hr3nyqO61oupj-lA</td>
      <td>1</td>
      <td>This place sucks. The customer service is horr...</td>
      <td>2</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>yFumR3CWzpfvTH2FCthvVw</td>
      <td>0</td>
      <td>2016-06-15</td>
      <td>0</td>
      <td>STiFMww2z31siPY7BWNC2g</td>
      <td>5</td>
      <td>I have been an Emerald Club member for a numbe...</td>
      <td>0</td>
      <td>TlvV-xJhmh7LCwJYXkV-cg</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</div>



# Dates
Select the month from the date string using a lambda function.


```python
# Your code here
df['date'].apply(lambda x: x.split("-")[0])
```




    0       2012
    1       2014
    2       2014
    3       2011
    4       2016
    5       2016
    6       2014
    7       2017
    8       2017
    9       2017
    10      2015
    11      2012
    12      2012
    13      2012
    14      2012
    15      2014
    16      2016
    17      2015
    18      2015
    19      2017
    20      2016
    21      2016
    22      2016
    23      2012
    24      2017
    25      2017
    26      2010
    27      2016
    28      2016
    29      2016
            ... 
    2580    2015
    2581    2013
    2582    2016
    2583    2015
    2584    2017
    2585    2015
    2586    2015
    2587    2012
    2588    2015
    2589    2015
    2590    2007
    2591    2016
    2592    2015
    2593    2013
    2594    2011
    2595    2014
    2596    2014
    2597    2016
    2598    2011
    2599    2014
    2600    2012
    2601    2014
    2602    2012
    2603    2013
    2604    2013
    2605    2013
    2606    2016
    2607    2016
    2608    2013
    2609    2016
    Name: date, Length: 2610, dtype: object



# What is the average number of words for a yelp review?
Do this with a single line of code!


```python
# Your code here
df['text'].apply(lambda x: len(x.split())).mean()
```




    77.06551724137931



# Create a new column for the number of words in the review.


```python
#Your code here
df['number_words_in_review'] = df['text'].apply(lambda x: len(x.split()))
```

## Rewrite the following as a lamda function. Create a new column 'Review_Length'


```python
def rewrite_as_lambda(value):
    if len(value) < 50:
        return 'Short'
    elif len(value) < 80:
        return 'Medium'
    else:
        return 'Long'
#Hint: nest your if, else conditionals
#df['text'].map(lambda x: 'Good' if any([word in x.lower() 
#for word in ['awesome', 'love', 'good', 'great']]) else 'Bad').head()
#a = "neg" if b<0 else "pos" if b>0 else "zero"
```


```python
#Your code here
df['review_length'] = df['number_words_in_review'].apply( lambda x: "Short" if x < 50 else 'Medium' if x < 80 else 'Long')
df['review_length'].value_counts()
```




    Short     1287
    Long       769
    Medium     554
    Name: review_length, dtype: int64



# Level Up: Dates Adavanced!
<img src="date_format_map.png" width=500>  

Overwrite the date column by reordering the month and day from YYYY-MM-DD to DD-MM-YYYY. Try to do this using a lambda function.


```python
#Your code here
import datetime
#datetime.datetime.strptime("2013-1-25", '%Y-%m-%d').strftime('%m/%d/%y')
df['date'] = df['date'].apply(lambda x: datetime.datetime.strptime(x, '%Y-%m-%d').strftime('%d-%m-%Y'))
```


```python
df['date']
```




    0       13-11-2012
    1       23-10-2014
    2       05-09-2014
    3       25-02-2011
    4       15-06-2016
    5       23-09-2016
    6       23-08-2014
    7       16-08-2017
    8       18-11-2017
    9       18-11-2017
    10      10-12-2015
    11      12-02-2012
    12      12-02-2012
    13      12-02-2012
    14      12-02-2012
    15      03-06-2014
    16      18-11-2016
    17      05-11-2015
    18      05-11-2015
    19      21-01-2017
    20      06-11-2016
    21      28-05-2016
    22      08-05-2016
    23      11-10-2012
    24      08-04-2017
    25      09-04-2017
    26      17-11-2010
    27      10-04-2016
    28      10-03-2016
    29      24-02-2016
               ...    
    2580    08-09-2015
    2581    12-07-2013
    2582    27-07-2016
    2583    12-10-2015
    2584    20-06-2017
    2585    17-10-2015
    2586    25-06-2015
    2587    14-08-2012
    2588    02-07-2015
    2589    22-03-2015
    2590    02-10-2007
    2591    17-07-2016
    2592    03-08-2015
    2593    28-08-2013
    2594    25-08-2011
    2595    27-02-2014
    2596    01-07-2014
    2597    20-08-2016
    2598    01-08-2011
    2599    27-01-2014
    2600    14-06-2012
    2601    14-01-2014
    2602    19-05-2012
    2603    01-03-2013
    2604    03-11-2013
    2605    02-06-2013
    2606    14-08-2016
    2607    14-06-2016
    2608    02-10-2013
    2609    15-08-2016
    Name: date, Length: 2610, dtype: object



## Summary

Great! Hopefully you're getting the hang of lambda functions now! It's important not to overuse them - it will often make more sense to define a function so that it's reusable elsewhere. But whenever you need to quickly apply some simple processing to a collection of data you have a new technique that will help you to do just that. It'll also be useful if you're reading someone elses code that happens to use lambdas.
