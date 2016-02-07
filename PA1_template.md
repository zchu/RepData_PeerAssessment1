# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
data <- read.csv("activity.csv")
```



## What is mean total number of steps taken per day?

```r
options(scipen = 3, digits = 3)
dailystep <- aggregate(steps ~ date, data = data, FUN = sum)
meanstep <- mean(dailystep$steps, na.rm = TRUE)
medianstep <- median(dailystep$steps, na.rm = TRUE)
```

1. The mean of the total number of steps taken per day is 10766.189.    
2. The median of the total number of steps taken per day is 10765.    
3. The histogram of the daily total steps is as below:


```r
hist(dailystep$steps, xlab = "Steps", main = "Histogram of Daily Total Steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png)

## What is the average daily activity pattern?

1. The time series plot of average daily activity is as below:


```r
intervals <- aggregate(steps ~ interval, data = data, FUN = mean)
intervals$interval <- strptime(sprintf("%04d", as.numeric(intervals$interval)), format="%H%M")
steptimeseries <- ts(data = intervals$steps)
plot(intervals$interval, intervals$steps, type="l", xlab="Interval (hh:mm)", ylab="Steps per interval")
```

![](PA1_template_files/figure-html/unnamed-chunk-4-1.png)

```r
options(scipen = 3, digits = 0)
maxstep <- max(intervals$steps)
maxinterval <- subset(intervals, steps == max(steps))$interval
```

2. 5-minute interval of 08:35, on average across all the days in the dataset, contains the maximum number of steps of 206. 

## Imputing missing values




## Are there differences in activity patterns between weekdays and weekends?


```r
##dailystepweekday <- subset(dailystep, weekdays())
##dailystepweekend <- 
```
