# YouTube-data-Analysis
text data analysis
• Conducted sentiment analysis on the comments of certain Youtube videos using TextBlob library.
Discovering audience’s attitude towards the videos and youtubers; Visualized audience’s attitude with WordCloud

• Discovered most used emojis

• Computed audience engagement rate& like rate among different categories of videos and found trending channels

• Investigated relationship between number of views & number of likes,
and relationship between video title naming & number of views using linear regression models.



**1.	Performing Sentiment Analysis**: 

It depends on 2 factors mainly,
              1. Polarity 
              2. Subjectivity.
 1. Polarity carries a sentiment in it can be a positive or negative polarity with a range of [-1,1]  
 2.	Subjectivity does not carry any sentiment in it. 
 3. textblob is one of package which we will be using. It is a NLP  library.


**2.	Using Wordcloud For Postive and Negative Sentences**:
      
      
  The bigger the font is the higher the priority it gets added to it. We create 2 sets of comments 
              1.comments_positive (1)
              2.comments_negative (-1) 
           TextBlob('trending 😉').sentiment 
* We use textblob to get the polarity and apply this our main dataframe passing comment_text to texblob such that we will get postive and negative comments 
* we will join all the postive comments as single string and pass it to the wordcloud 
                 wc=WordCloud(stopwords=set(STOPWORDS)).generate(total_comments) 
![image](https://github.com/tiru18324/YouTube-data-Analysis/assets/71921628/cb5773d3-43ae-4a72-b4b4-70662edbea85)



      * stopwords are basically not important words like the,is,of…. Etc. we will be ignoring this and concentrating mainly on the polarity either positive or negative w.r.t to the stopwords.
 
 
******3.Perform Emoji Analysis.******
How many people use that emoji package. What is the count of each emoji either happy,sad,excited 

* each emoji having their unicodeencoding character assinged to everthing irrespective platform,device,language.  
* we create a dictionary with emoji count. in a comment there will be a emoji to get that emoji we use emoji.UNICODE_EMOJI_ENGLISH and append that emoji to a list and use Counter to count the emoji to get the most_common ones and use list comprehension to get the counts of emoji and frequencies. 
* USING Plotly's Python graphing library  can make interactive, publication-quality graphs. Examples of how to make line plots, scatter plots, area charts, bar charts, error bars, box plots, histograms, heatmaps, subplots, multiple-axes, polar charts, and bubble charts.
So, to make barchart we use plotly.graph_obj and iplot to trace it

![image](https://github.com/tiru18324/YouTube-data-Analysis/assets/71921628/1a85e024-36ba-4688-a8fe-564c225b506f)

**4. COLLECT ENTIRE DATA OF YOUTUBE: **

1.	For os we import os and make a list of those files files=os.listdir(path) and get the file from path 
       current_df=pd.read_csv(path+'/'+file,encoding='iso-8859-1',error_bad_lines=False such that file is from we only get csv files 
2. Gettting country name using split and category name from path and converting to dictionary using to_dict. And mapping that category name with category_id 
full_df['category_name']=full_df['category_id'].map(dict['category_name']) 

3 Category With Most Likes:
#using boxplot to visualize numerical values in quartile percentages min,25%,median,75%.so from this we can see music and entertainment has most likes.  

![image](https://github.com/tiru18324/YouTube-data-Analysis/assets/71921628/1501a577-c6b7-42a0-9758-e4000b4a311d)

****5. Audience is Engaging Or Not:****
        It depends on 3 factors :
                         1. Like Rate 
                         2. Dislike Rate 
                         3. Comment Ratio 


Calculating the percentage of all rates 
_1)Like Rate wrt Views_: So, Entertainment has more likes and less median value compared with comedy

        It depends on 3 factors :
                         1. Like Rate 
                         2. Dislike Rate 
                         3. Comment Ratio 
![image](https://github.com/tiru18324/YouTube-data-Analysis/assets/71921628/b4ed95dd-78e0-4293-8f96-68ca23b3f36d)


****6.which channel has largest no of videos**:- **
To count of videos in a channel 
cdf=full_df.groupby('channel_title')['video_id'].count().sort_values(ascending=False).reset_index().rename(columns={'video_id':'total_videos'}) 
AND plotting a graph chart for that. 


![image](https://github.com/tiru18324/YouTube-data-Analysis/assets/71921628/54ebad59-9b78-4641-97c7-c0d3d5fa389c)











