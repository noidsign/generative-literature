# generative-literature
## A list of resources to create your own generative literature.  

This repo is for beginners. It collects all resources needed to get data, feed it to a recurrent neural network, and get your own personal generative literature work. The examples are made getting data from Twitter feeds. You can use any text based data you like.

### What do you need </br>
#### This tutorial is made for MacOS users </br>
You will need: </br>
  · A Twitter account (optional) </br>
  · A 2.7 python enviroment installed – the tutorial might not work with higher python versions </br>
  · Tweepy installed (we'll cover that) </br>
  · Torch and lua installed (covered in one of the links) </br>
  · Some time: training data can take anything between hours (1-3 MB) and days depending on the size of your dataset </br>
</br>   
### 1. Set up your twitter app
Follow the instructions you find here **http://docs.inboundnow.com/guide/create-twitter-application/**
</br>
***Important:*** Make a note of your OAuth settings: </br>
  · Consumer Key </br>
  · Consumer Secret </br>
  · OAuth Access Token </br>
  · OAuth Access Token Secret </br>
  You will need them in order to download the tweets from Twitter feeds.
</br>
### 2. Download and install Tweepy
Super easy. Just follow the instructions here **https://github.com/tweepy/tweepy**
</br>
### 3. Create a python script to download the tweets you want to get
Go to: **https://gist.github.com/yanofsky/5436496**</br>
Copy the code and paste it in a code editor (like Sublime text). </br>
You only need to **change**: </br>
**· the Twitter API credentials** You have them from point 1 of this tutorial </br>
**· the Twitter handle you want to get tweets from**: in the example from @yanofsky you have *J_tsar*. Choose the one you want to get tweets from. 
</br>
### 4. Run the script 
Save your file as ```tweet_dumper.py``` </br>
Go on your Terminal and ```cd``` your way to the folder where you have saved ```tweet_dumper.py``` </br>
Now run the script by typing ```python tweet_dumper.py``` in your terminal </br>
Twitter only allows to get the last 3200 tweets from an account. They will be saved in a csv file.
</br>
### 5. Clean the data 
The csv file comes with a bunch of stuff other than the text of the tweets. Get the tweets and copy and paste them in a input.txt file </br>
### 6. Install the recurrent neural network, train it, and sample it 
A bit more complicated than point 2, but still farily easy. Go to: **https://github.com/karpathy/char-rnn** and follow the instructions.
</br>
### 7. Extra tip for selecting the right .t7 file for sampling
This is actully the only piece of code I wrote myself, with the help of StackOverflow. 
```
import os
import re

paths = (os.path.join(root, filename)
        for root, _, filenames in os.walk('/Users/your-user/some-folder/char-rnn-master/cv/')
        for filename in filenames)
			

for path in paths:
    newname = re.sub(r'.*_', '', path)
    if newname != path:
        os.rename(path, newname)
```
If you don't have the python module ```re``` installed, go to your terminal and install it. As simple as typing ```pip install re``` in the terminal </br>
This will eliminate all the part before the char ```_``` from your trained models (the .t7 files). That way it's gonna be super simple to identify the one with least loss (the smaller the number, the smaller the loss). </br>
Then keep with the instructions from point 6 and have fun sampling. </br>
Cheers! 
