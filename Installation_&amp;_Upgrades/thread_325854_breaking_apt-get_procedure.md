---
title: "breaking apt-get procedure"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by nsleiman on 2006-12-26
Hi all,

i started apt-get install gnome and i wanted to know if i break it, when i start it next time, can i continue uploading packages does it need to restart the whole process ?

its because i have to download 129 MB and im at an internet cafe. 

appreciating your help,

regards,

---

### Post by meng on 2006-12-26
Haha whoops! Not the right time to be downloading that many packages!
You should be able to press ctrl-c to break it (apt-get downloads all packages before it installs anything). I'm not certain if it will pick up exactly where it left off next time (I understand there is some sort of cache though), but just enter the same command to resume.

---

### Post by nsleiman on 2006-12-26
:( i will call it hard luck if it wont resume! btw with cached u mean locally for sure i guess, no ? and what do you think what is better gnome or kde ? from the point of view of speed.

---

### Post by meng on 2006-12-26
> **nsleiman said:**
> :( i will call it hard luck if it wont resume! btw with cached u mean locally for sure i guess, no ? and what do you think what is better gnome or kde ? from the point of view of speed.
By cached I mean that there is some stored file locally (don't worry, there is a command to clean the cache if you ever need to unclutter your drive, I don't know it off the top of my head though). I use GNOME, I have less experience with KDE. I don't think either is clearly better than the other, GNOME just happens to be my personal preference. Speedwise I believe they're similar, but you'll find those who argue either way.

---

### Post by nsleiman on 2006-12-26
thank you a lot meng, if it happens and u remember the clearing cache command let me please know :)

---

### Post by meng on 2006-12-26
sudo apt-get clean
(the cache clearing may occur automatically from time to time anyway)

---

### Post by nsleiman on 2006-12-27
After i restarted the same ´apt-get install gnome´ it resumed from the point i broke it last day. thank you a lot meng, what a powerful command :) god save Ubuntu!

---

