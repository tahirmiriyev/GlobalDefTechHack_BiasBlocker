# GlobalDefTechHack_NoBias

## Idea:
The information war is always a consistent part of any military conflict. As we also experienced during the events of the Karabakh War II,  details of the war are conveyed only from one perspective and not objectively; for example, by international networks, such as France24, Aljazeera, The Guardian, etc. In particular, biased news is the major source of misinformation and propaganda. According to American psychologist Silvio Bronzo's book, “How propaganda works”, one of the most effective ways to prevent propaganda is to provide news from all conflicting sides. Inspired by that, we came up with an idea to create a browser extension called “BiasBlocker”. Only this way, we will be able to eliminate any bias and stop propaganda. For this hackathon, our target audience is international newsreaders. Our goal is to bring justice to the world via our product. So, how 
does BiasBlocker work?

### Step 1: (Back-end) Natural Language Processing with NLTK Python library.
We begin by parsing info from the current news article (ex: "Nagorno-Karabakh truce in jeopardy as accusations of violations fly" from The Guardian). We use NEWSPAPER Python library to extract the content, publication date, title, images and videos. In advance, on our database we have 6000+ news articles extracted from top 14 Azerbaijani and Armenian news portals. However, this data is not simply stored there; we apply K-means Clusterising (a Machine Learning model) to cluster news into categories. Then the keywords list for each category is defined and current news article is compared to those keywords through a rigorous RELEVANCE FUNCTION that we have written. The working principle of this function is based on assigning weights to nouns (e.g. missile, civilians, bombs), verbs (e.g. attack, liberate) and proper names (e.g. Hikmat Hajiyev, Ilham Aliyev), using Named Entity Recognition tools of NLTK, also including synonyms and antonyms from WordNet. Then our algorithm calculates final metrics for each article. At the stage of defining what Azeri and Armenian news are relevant the current one, these metrics are utilized. Please see respective codes for more details. Once everything is pairwise compared, top 5 relevant news from both conflicting sides are selected and displayed on the front-end of our extension. 

### Step 2: (Back-end) Optimization with RUST
Fast computation is the key in our product. Obviously, we can't ask a user to wait for too long while the algorithm finds relevant news. In order to process everything in at most 3 sec, we translate the entire code into RUST programming language. 

### Step 3: (Front-end) Demo

Please see "AzOps-Fables-BiasBlocker-FULL DEMO.mp4" video.

### Business Plan

Please see "BiasBlocker Business Plan.pdf" file.


# INSTRUCTIONS on setup and running
1.	Download and unzip bias-blocker.zip 
2.	Open Google Chrome Settings - Extensions
3.	Make sure that Chrome Extension has the Developer Tools enabled
4.	Click the “Load unpacked” button
5.  Select the unzipped folder on step 1 and make sure that is enabled on your side
6.  Then surf to one of “TheGuardian” articles related to Nagorno-Karabakh conflict and you should get the related articles

Since we had only 48 hours to build a prototype, our extension is fully tested and works well on “The Guardian” website.
The example links on which the extension can be demoed are:
https://www.theguardian.com/world/2020/oct/11/nagorno-karabakh-truce-in-jeopardy-as-accusations-of-violations-fly
https://www.theguardian.com/world/2020/oct/26/nagorno-karabakh-us-brokered-ceasefire-agreed-amid-fresh-fighting
https://www.theguardian.com/world/2020/oct/05/azerbaijan-and-armenia-accuse-each-other-of-shelling-cities

In the future we plan to have it running also on the all international news websites like BBC, Euronews, France24, etc. 
