# Build-a-Brand-Sentiment-Analysis-Extension-for-Twitter-

Are you a Twitter enthusiast who wants to quickly see the sentiment behind the tweets on your timeline? Or maybe you’re an organization and want to understand the sentiment towards your brand on Twitter. This browser extension is for you. It performs sentiment analysis on tweets and displays the results in an easy-to-consume format. This project provides a hands-on opportunity to learn about machine learning in practice, as well as how to create browser extensions.

##Features
Real-time sentiment analysis of tweets
Visual representation of the sentiment of tweets in a pie chart


##Requirements/Prerequisites
Docker should be installed on your local machine
An entitlement key from IBM, which can be obtained here


##Installation
Starting the Sentiment Analysis Model locally
If you start the sentiment analysis model locally then you must ensure you have the IBM entitlement key from the requirements/prerequisistes section as well as have docker installed. Then run the following commands in your terminal in this directory:

>>IBM_ENTITLEMENT_KEY=<your-key>
>>echo $IBM_ENTITLEMENT_KEY | docker login -u cp --password-stdin cp.icr.io
>>docker build -t nlp-model .
>>docker run -d -e ACCEPT_LICENSE=true -p 8080:8080 nlp-model

This starts up a container with the Watson Sentiment Analysis model on port 8080. You can then use the following value for your container URL in the Javascript files.

const containerUrl = "http://localhost:8080/v1/watson.runtime/nlp.v1/NlpService/SentimentPredict";
If you deploy your sentiment analysis model somewhere else, be sure to adjust the containerUrl.

##FireFox
Clone or download the repository to your local machine
Open a new FireFox window
Navigate to about:debugging#/runtime/this-firefox
Click on Load Temporary Add-on... and then find the manifest.json file from the cloned repository

##Chrome
Clone or download the repository to your local machine
Change all references of browser to chrome
To use the extension in Chrome, all instances of browser must be changed to chrome. These instances are in the Javascript (.js) files. So, be sure to double check the popup.js, tweet-sentiment.js, and background.js files.

Open a new Chrome browser window
Navigate to chrome://extensions/ and ensure the Developer mode setting is on
Click on load unpacked and select the root folder of this cloned repository


##Usage
Open Twitter in your browser
Click on the extension icon
Search for a topic or brand of your interest (e.g. Spotify).
Scroll through the feed and open the popup to see sentiment analysis results through the updating pie chart

##Note:
The extension is currently only compatible with twitter.com but this project can be used as a template to branch to other social medias

##Example
This is an example of the browser extension in action. In the image, Spotify was searched, and the data was populated by scrolling down the timeline for a little bit. We can see Spotify has more of a positive sentiment meaning people are tweeting good things around Spotify's brand. The data is displayed in a pie chart and can be shown or closed by clicking the browser extension popup button. As the user scrolls the data populates more. If the user would like to move to a new query, the reset button can be clicked to reset the current results.

<img width="945" alt="sentiment-analysis-report" src="https://github.com/solairaja13/Build-a-Brand-Sentiment-Analysis-Extension-for-Twitter-/assets/111340211/a45ec808-b0d2-4aff-bc50-7c30882b221f">
