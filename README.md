# Housing-Prediction-Challenge
Started by importing the libraries we needed and loading the training and testing datasets. The training set contains 1,200 houses with their actual sale prices, while the test set has 260 houses that we need to predict prices for.
We noticed two very large houses sold for much less than their size suggest and they throw the model off, so we dropped them from the training data.
We combined related columns into features that capture what buyers care about: total square footage, total bathrooms (half baths count as 0.5), house age, years since remodel, and total porch and deck area. We also added quality × living area, because extra square footage is worth more in a higher-quality house. MSSubClass and MoSold are numeric codes, not quantities, so we converted them to strings to treat them as categories.
House prices and some size measurements have a few very large values that can dominate and skew the model. Taking the log reduces that effect. We applied it to the sale price and to the columns that were strongly right-skewed.
using alpha with cross-validation, we tested on 5 different parts of the training data
The error got steadily lower as alpha increased, from $24,114 at alpha = 5 to $23,356 at alpha = 50, so we used alpha = 50.
This means a typical prediction is off by about $23,000, or roughly 13% of the average house price. Because alpha = 50 was the largest value we tried, a larger alpha might do slightly better.
