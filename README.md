# Predicting Response Times of the San Francisco Fire Department

The goal of this project is to predict the time it will take for the fire department to arrive on the scene of an incident using machine learning in Spark.

This was the final project for our course in Distributed Data Systems in the University of San Francisco Master of Science in Data Science program taught by Diane Woodbridge.

## Contributes

[Adam Reevesman](https://github.com/areevesman)
[Sarah Melancon](https://github.com/smelancon)
[Xu Lian](https://github.com/xulianrenzoku)
[Jon-Ross Presta](https://github.com/jrpresta)

## Data

The [data](https://www.kaggle.com/datasf/san-francisco) comes from the San Francisco Open Data dataset on Kaggle. Though this dataset is updated regularly, the data for this study was collected on January 24, 2018. We used the features `station_area`, `call_type`, `zipcode_of_incident`, `received_hour`, and `day_of_week` from this dataset. We also obtained our labels from this dataset.

The features `distance` and `duration` were created using the [Google Distance Matrix API](https://developers.google.com/maps/documentation/distance-matrix/intro) to get distances and time estimates between each fire station and the addess of the incident.

Checkout [this notebook](/notebooks/data_prep.ipynb) to see how we extracted features from the Kaggle dataset and [this notebook](/notebooks/google_routes_data_prep.ipynb) to see how we added features from the Google Distance Matrix API.

## Methods

We used the MLlib machine learning library in PySpark and ran our code on an AWS t2.xlarge EMR cluster.

We used four different algorithms to compare the results:
- Linear Regression
- Linear Regression with Elastic Net
- Decision Tree
- Random Forest

## Results

We found that the data from the Google Distance Matrix API provided the most useful features when modeling response times. However, the features from the Kaggle dataset did lead to some improvement over predictions based on Google alone.

Linear Regression: 

R^2:  0.0382449456338

RMSE: 4.82394317574 (minutes)

MAE: 3.3039737344 (minutes)


Linear Regression with Elastic Net:

R^2:  -0.0368547038269

RMSE: 5.00874469868

MAE: 3.45915225661


Decision Tree:

R^2:  0.0245728649704

RMSE: 4.85811019003

MAE: 3.34637837615


Random Forest:

R^2:  0.0229994180441

RMSE: 4.86202688363

MAE: 3.34406035385

See [this notebook](/notebooks/modeling.ipynb) for our process and results.
