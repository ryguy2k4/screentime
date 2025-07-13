# screentime

## Overview
Going back to the beginning of 2024, I began saving my Apple Screen Time data because I thought it would make for an interesting dataset to analyze in the future. I think that there are a lot of potential insights that can be drawn from my personal screentime data, hopefully such that I can make more informed decisions about how I want to use my devices in the future. This analysis makes use of Tableau, partially to demonstrate my proficiency in it.

### Repository Structure
* `src`: contains python scripts/notebooks and tableau workbooks used to produce results
* `results`: contains final products

## Data
Apple devices have a built-in screentime tracking feature, but they do not make it natively easy to export the data. I found a python script called [screentime2csv](https://github.com/FelixKohlhas/ScreenTime2CSV) that would extract the data from my iCloud Account. I used the script to periodically export my screentime data, but there are some gaps in the data due to the fact that I did not always remember to export the data.

Here is a Data Dictionary for the exported CSV files. Each row represents a screen time session.

- `app`: Name of the application used during the screen time session.
- `usage`: Duration of the screen time session in seconds.
- `start_time`: Timestamp of when the screen time session started.
- `end_time`: Timestamp of when the screen time session ended.
- `created_at`: Timestamp of when the record was created.
- `tz`: Timezone of the screen time session.
- `device_id`: Unique identifier for the device.
- `device_model`: Model of the device. Missing values imply the device was a macOS device.

Using the pandas library in Python, I cleaned the data and then aggregated it to daily totals by app and device (iPhone and Mac). I also manually created app categories (youtube, streaming, news, social, productivity, utilities, browser, etc) to use in the analysis. 

Here is a Data Dictionary of my processed file used for analysis.

- `date`: The date in question.
- `app_category`: The app category in question.
- `usage_phone (min)`: iPhone screentime usage in minutes.
- `usage_mac (min)`: Mac screentime usage in minutes.

**I only considered iPhone screentime in the analysis**.


## Tableau Story via PowerPoint Slides:

### Spring 2025 Semester Overview
![Alt text](/results/slides/Slide2.png "Spring 2025 Semester Overview")
### Essential vs Distraction Screentime
![Alt text](/results/slides/Slide3.png "Essential vs Distraction Screentime")
### Weekday vs Weekend Trends
![Alt text](/results/slides/Slide4.png "Weekday vs Weekend Trends")
### Screentime Habit Changes after Deleting YouTube over Spring Break
![Alt text](/results/slides/Slide5.png "Screentime Habit Changes after Deleting YouTube over Spring Break")
### Comparison to Previous Semesters
![Alt text](/results/slides/Slide6.png "Comparison to Previous Semesters")
### Looking Forward
![Alt text](/results/slides/Slide7.png "Looking Forward")

## Future Work
I need to automate the data extraction so that I do not have to remember to do it manually. Not having it automated is leading to occasional gaps in the data that can influence the analysis.

I'd like to perform a separate analysis of my Mac screentime data and then also look at relationships between my iPhone and Mac screentime usage. One major issue with the Mac screentime data is that so much screentime on my Mac is spent on web-based activities in a browser, and the data simply records the activity as using the web browser. I could try to merge my browser history into the dataset to get a more complete picture.