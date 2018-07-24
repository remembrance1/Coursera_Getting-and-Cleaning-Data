Code Book
================

This document describes the code inside run\_analysis.R.

The code is splitted (by comments) in some sections:

-   Downloading and loading data
-   Manipulating data
-   Writing final data to CSV

Downloading and Loading of Data
-------------------------------

-   Downloads the UCI HAR zip file if it doesn't exist
-   Reads respective train and test activity labels to `trainactivity` & `testactivity`
-   Reads respective train and test subject labels to `trainsubject` & `testsubject`
-   Reads respective train and test features labels to `trainfeature` & `testfeature`

Manipulating Data
-----------------

Utilized helper functions such as: rbind, cbind and grep

-   Merged activity, feature and subject together from test and train datasets
-   changes factor levels(1-6) to match activity labels
-   names activity and subject columns
-   names feature columns from features text file
-   selects columns with mean and standard deviation data and subsetting
-   Combines data sets with activity names and labels
-   Clarifying time and frequency variables
-   Creates new data set with subject and activity means with the name, `cleandata`

At this point the final data frame `cleandata` looks like this

``` r
head(cleandata[,1:5], 5)
```

    ##   Subject Activity timeBodyAcc-mean()-X timeBodyAcc-mean()-Y
    ## 1       1  WALKING            0.2773308          -0.01738382
    ## 2       2  WALKING            0.2764266          -0.01859492
    ## 3       3  WALKING            0.2755675          -0.01717678
    ## 4       4  WALKING            0.2785820          -0.01483995
    ## 5       5  WALKING            0.2778423          -0.01728503
    ##   timeBodyAcc-mean()-Z
    ## 1           -0.1111481
    ## 2           -0.1055004
    ## 3           -0.1126749
    ## 4           -0.1114031
    ## 5           -0.1077418

Writing final data to CSV
-------------------------

Creates the output dir if it doesn't exist and writes `cleandata` data frame to the ouputfile.
