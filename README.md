# actimetric

<!-- badges: start -->

<!-- badges: end -->

The goal of `actimetric` is to apply machine learning-based algorithms to accelerometer data to provide insights in physical activity and sleep behaviors in free-living conditions.

## Installation

To use actimetric, first you need to install the development version of actimetricModels like this:

``` r
library(remotes)
install_github("PhysicalActivityOpenTools/actimetricModels")
```

Then, you can install the development version of actimetric like so:

``` r
library(remotes)
install_github("PhysicalActivityOpenTools/actimetric")
```

## Example usage

To use actimetric, you can just rely on the `runActimetric` function.

The bare minimum of input arguments would be the input_directory, output_directory, and the classifier that you would like to use. See next function call for a example:

``` r
library(actimetric)

# This runs the program
runActimetric(input_directory = "G:/directory_containing/the_input_files/",
              output_directory = "G:/directory_to_save/the_output_files/",
              studyname = "my_study_name",
              classifier = "Preschool Wrist Random Forest Free Living")
```

The `actimetric` R package supports the use of 9 different classifiers for now:

-   [Preschool Wrist Random Forest Free Living](https://pubmed.ncbi.nlm.nih.gov/29059107/)

-   [Preschool Hip Random Forest Free Living](https://pubmed.ncbi.nlm.nih.gov/29059107/)

-   [Preschool Hip Random Forest Free Living Lag-Lead](https://pubmed.ncbi.nlm.nih.gov/29059107/)

-   [Preschool Wrist Random Forest Free Living Lag-Lead](https://pubmed.ncbi.nlm.nih.gov/29059107/)

-   [School age Wrist Random Forest](https://pubmed.ncbi.nlm.nih.gov/25340887/)

-   [School age Hip Random Forest](https://pubmed.ncbi.nlm.nih.gov/25340887/)

-   [Adult Wrist RF Trost](https://pubmed.ncbi.nlm.nih.gov/27372275/)

-   [Adult women Wrist RF Ellis](https://pubmed.ncbi.nlm.nih.gov/26673126/)

-   [Adult women Hip RF Ellis](https://pubmed.ncbi.nlm.nih.gov/26673126/)


## Additional parameters

Additionally, you can control a number of extra parameters in `actimetric` . For example, you can decide on calibrating the data with argument `do.calibration`, on the acceleration metrics you would like to calculate with options for ENMO, Actilife Counts, and Actilife LFE counts, or whether to detect non-wear and sleep periods.

Here a function call with all potential arguments you may use in `actimetric`, all of them defined with their default values:

``` r
library(actimetric)

# This runs the program
runActimetric(input_directory = NULL,
              output_directory = NULL,
              studyname = "actimetric",
              classifier = NULL,
              do.calibration = TRUE,
              do.sleep = TRUE,
              do.nonwear = TRUE,
              do.enmo = FALSE,
              do.actilifecounts = TRUE,
              do.actilifecountsLFE = FALSE,
              boutdur = 10, boutcriter = 0.8,
              verbose = TRUE, overwrite = TRUE,
              n_valid_hours = 16,
              n_valid_hours_awake = 10,
              n_valid_hours_nighttime = 2,
              visualreport = TRUE)
```

## The output

The `actimetric` R package will generate two folders inside the `output_directory`. One of them will contain the time series with the time-stamped epoch-level estimates for the activity classification and the acceleration metrics calculated. The time series come in the format of `.RData`. Additionally, `actimetric` will generate another folder, named results, that will contain day-level and recording-level aggregates of the data in `.csv` format, as well as visualizations of the recordings in `.pdf` format. Note that visualizations are not generated by default, yet you can turn them on with argument `visualreport`.
