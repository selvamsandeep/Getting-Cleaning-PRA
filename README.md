Getting and Cleaning Data peer assessment
------------------------------------------

This is my submission for the JHU/Coursera [Getting and Cleaning Data](https://www.coursera.org/course/getdata) class [peer assessment](https://class.coursera.org/getdata-002/human_grading/view/courses/972080/assessments/3/submissions) (enrollment required for access). My script requires very little setup. Run it anywhere; if there is no directory named "UCI HAR Dataset" in your working directory, the script will take care of downloading [the zip file](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) and unzipping it (and will delete the zip file to keep things clean). The source data will remain in the working directory upon completion of the script, for the sake of subsequent runs.

The only R library dependency (the ``reshape`` library) will be installed by the code if it isn't available in your environment; you may be prompted to select a CRAN mirror.

Obviously, if the code needs to handle source data acquisition or library installation itself, it'll need an internet connection.

```bash
> source("run_analysis.R")
[1] "Script completed. To check results, run read.table function on tidyoutput.txt"
>
```
Steps performed by run_analysis.R:
* set up files if necessary
* read in relevant source data
* bind together test and training data
* label activities and measurements based on index files
* combine subjects and activities into one data frame
* extract all measurements from source data that contain "mean()" or "std()" (not to include those with "meanFreq()") and add them all the composite data frame
* include/install reshape library as needed
* melt and cast the data so as to take the mean of each measurement for each subject+activity
* output the results to file

The results are outputted to ``tidyoutput.txt`` in the format described by the instructions (and clarified to some consensus in the forums). To test the output, consider running the following checks in the same working directory:

```bash
> tidyOutput <- read.table("tidyoutput.txt")
> nrow(tidyOutput)
[1] 180
> ncol(tidyOutput)
[1] 68
> head(tidyOutput)
...
```

Thanks for your time!
-VJ
