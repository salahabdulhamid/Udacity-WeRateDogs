                                                              WeRateDogs Udacity Project
Wrangling Efforts
“A brief report to outline the wrangling efforts, type of data and analysis, and the insights extracted from twitter WeRateDogs data archives”

1. Data Gathering:
We had an extracted file already contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017, however it wasn’t enough to generate useful insights so we had to augment the data with two additional files.
First i downloaded from the twitter_archive.csv manually, then image prediction.tsv was downloaded using Requests/OS libraries, Lastly the twitter API was downloaded using tweepy library (the method I followed was for a video on YouTube applying this function to search for hashtags, I had the idea and applied it I find it very useful if I am working with a team to allow other coders to use their credentials to have the most updated json, then I assigned the required headers for assessing, cleaning, and generating insights.
Converted all three types to pandas DataFrames and moved to the next phase.

2. Data Assessing:
I Have made both Visual and Programmatic assessment, and some of the visual have been done using google sheets, and here are screenshots for (Quality Issues) Detected while visual assessment.
I also assessed the two other files, (status.json, and image_prediction.tsv) visually and programmatically in jupyter notebook using methods such as .info(), .head(), .sample(), and .value_counts().
The datasets were accessed to scan two criteria, quality and tidiness. When an issue was detected it was documented under one of these two criteria based on the issues found.

3. Data Issues:
Tidiness Issues
After assessing the data provided here is a summary of the found issues.
There are 4 columns (doggo,floofer, pupper, puppo) which are dog stages in DoggoLingo and the info provided in the project motivation, means there is one variable stored in 4 columns, Some columns doesn't represent any values ('expanded_urls', 'retweeted_status_id', 'retweeted_status_user_id', 'retweeted_status_timestamp'), and might not be needed for analysis, NONE word needs to be replaced to allow us to know the null values, Timestamp has more than one variable (Date, and Time), (p1, p1_conf, p1_dog) Don't represent variable names, The three data sets has columns that needs to be removed, Not useful to analyze or capture insights, and lastlyThe three data sets are same observation unit displayed in 3 tables.
Quality Issues:
Columns with missing values [in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp, and expanded_urls] 

(Completeness Issue).
Based on the requirement it has to be original tweet neither retweets nor reply, tweets that has value in_reply_to_status_id, needs to be removed and keep original tweets only (Validity Issue), rating_numerator column has 21 outliers, rates above the accepted range (from 44 to 1776 )(validity & accuracy), "These ratings almost always have a denominator of 10".said in the (Project Overview), however we have values in rating_denominator columns less and more than 10, 'rating_denumirator' has zero values, 'Name' column has too many NONE values, might cause issues analyzing, Timestamp needs to be converted to PD.datetime values, 66 Duplicate values in column jpg_url, and more than 2000 duplicated (img_num), P1 column has prediction of no dogs names, Columns from p2 until p3_dog have low condidence levels, needs to be removed, we have in P1_dog 543 values for no dogs (False), And API dataset has 163 values favorite_count == zero, means never been favorited Data Cleaning: The final step in the wrangling process is cleaning the data for quality and tidiness issues, first I created a cleaned data sets by copying, remove all rows that has values (in_reply_to_status_id), Remove Columns with Missing values, and excluded from the analysis, Remove all the outliars in column (rating_numerator), Cleaning the column rating_denumirator from all values != 10, Etc until created one master Dataframe also merged the four dog stage columns into one, ETC (all explained in the notebook as well). • Insights and visuals: 1. First Insight: “golden_retriever, and Labrador_retriever are the most common dog according to WeRateDogs Data, and Aim and West_Highland_white_terrier is the less common dog ccording to WeRateDogs Data, and AI”
2. Second Insight: “Top Rated Dogs have less retweet count, and vice versa”
3. Third Insight: “The top rated dog class is not the most common class. The most rated dog is Saluki, Tibetan_mastiff, briard, Border_terrier, standard_schnauzer, silky_terrier” 4. Forth Insight: “Dog ratings has no correlation with the most common dog”
