---
title: "indicator-weather"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by kgarbutt on 2013-06-08
Hi Everyone,

I'm running Ubuntu 12.04 LTS, and as many of you know, the indicator-weather package hasn't been working in a while. To get it working in 12.04 LTS, please do the following:

Download this python wrapper:  [https://launchpad.net/ubuntu/saucy/i386/python-pywapi/0.3.2-1](https://launchpad.net/ubuntu/saucy/i386/python-pywapi/0.3.2-1)

then from the terminal,  sudo dpkg -i python-pywapi_0.3.2-1_all.deb

and finally from the terminal,  sudo apt-get install indicator-weather

Then it will work. 

I stumbled across it trying to get mine to work. I got lucky. I thank the developers for such a great program & updated wrapper.

Enjoy, 
Ken

---

### Post by Iowan on 2013-06-08
Thought I was still out of luck - crashed again.
Removed/re-installed - crashed again.
Replaced Yahoo with Weather.com - working.

MANY thanks!!!

---

### Post by kgarbutt on 2013-06-08
Hey Iowan, I guess I got lucky. I didn't have any of your troubles, and I am using Yahoo as the Weather Data Source. Thanks, Ken

---

### Post by Iowan on 2013-06-08
Hmmm... maybe I'll try Yahoo later.
(but I kinda hate to mess with it - since it's finally working)

Well, finally got brave enough to try Yahoo!. It works, but Weather.com and Yahoo display different temperatures (only one degree apart).
> A man with a watch always knows what time it is - a man with two NEVER does.

---

### Post by kgarbutt on 2013-06-10
I want to add something new to this thread. I noticed in Ubuntu-Tweak that under apps it lists a ppa for indicator-weather. I didn't know that indicator-weather even had a ppa. In any case, if you are having trouble with indicator-weather's installation, then install the python-wrapper from the first post, and then install the ppa through Ubuntu-Tweak & all should work. I had to do this to my work computer. I didn't have this problem on my home laptop - both running 12.04.

Yes, I know - interesting!!


Good luck everyone. 
Ken

---

### Post by Iowan on 2013-06-15
Lost it after update - I'll try again.

---

