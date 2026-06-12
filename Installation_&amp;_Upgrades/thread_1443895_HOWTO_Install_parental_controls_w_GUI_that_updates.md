---
title: "HOWTO Install parental controls w/ GUI that updates"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by LifeBringer on 2010-03-31
After using Ubuntu for a few days. I realized that I needed good parental controls to block sites like facebook, myspace, mofunzone, etc. I used to use K9 on Win7 64 bit. After half an hour of searching. I still couldn't find and easy, simple to use, way of installing parental controls.

So, I decided to try out something straightforward with updatability. The primary reason for me creating is this thread is so that Google (and other search engines) can pick up on this simple tutorial.

Step 1
Go to [www.ubuntuce.com/convert.htm](www.ubuntuce.com/convert.htm)

Step 2
Open the terminal and follow the instructions listed, however *IMPORTANT* change **install ubuntu-ce** to **install dansguardian** *IMPORTANT*.
follow the prompts answering 'Y'

Example
```

64 bit Systems:
Open a terminal window (Applications&#8594;Accessories&#8594;Terminal), and execute the following command:
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get **install dansgaurdian**
```
Answer &#8216;Yes&#8217; when needed.

Voila! Your Ubuntu is now running Parental Controls that automatically updates. (NOTE: it does take a few restarts for it to show up in **System -> Administration -> Parental Controls**)


Hope you Enjoy!

[IMG]http://img262.imageshack.us/img262/1903/parentalcontrols.png[/IMG]
Tested on Lucid 10.04b1

P.S. Be sure to comment! That would up the page rank.

---

