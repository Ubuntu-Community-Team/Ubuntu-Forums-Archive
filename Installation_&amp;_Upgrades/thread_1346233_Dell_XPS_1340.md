---
title: "Dell XPS 1340"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by ajvsouza on 2009-12-04
Hi Guys,

I have a DELL XPS notebook. I decided to try Ubuntu after several headaches that I had with Vista. I would say that so far so good. Probably I will use MicroSoft only at my work.

Since I moved to Ubuntu, I am still having some issues with my wireless:
- Connection with 9.0 was terrible
- Since I upgraded to 9.10 (Karmic Koala) it improved a lot, however I am still having problems that I never had before with Windows XP (my router is still the same old linksys wrt54g) , like:
- connection drops even when the applet shows that the signal is good

Also I have a old machine with a TV card. Using Windows XP I was able to watch the  MPG file (about 1.0 Gb in average) in a shared folder using my notebook wireless connection. Currently it is impossible with Linux. After opening the file, usually the video halts after a couple of minutes

Does anybody knows any solution for this? By the way, I already tried to change some configuration in the router. However with Windows, even the default ones worked without any issue.

Thanks in advance

AJVS

---

### Post by davidryderuk on 2009-12-05
Edit: Found an easier solution. See next post.

---

### Post by davidryderuk on 2009-12-05
Sorry I can't give you exact instructions, after posting my orginal solution I realised that you were running kubuntu, which I've never used. From what I can find you should try the following though.

1. Connect to the internet through ethernet, so as to obtain a stable internet connection.

2. Download and install any updates on your computer.

3. Find the Hardware Drivers application.

4. You should be presented with an option to download, install and enable the "broadcom-sta" driver. 

You might also be interested in this thread:

[http://kubuntuforums.net/forums/index.php?topic=3107428.msg202718#msg202718](http://kubuntuforums.net/forums/index.php?topic=3107428.msg202718#msg202718)

Hope this helps

---

### Post by ajvsouza on 2009-12-05
Hi David,

I would say that the solution does not work. I updated the driver following your instructions.
- video watching - it still halts after a couple of minutes
- basic browsing - I did not find any difference. Any way it takes some time to see if it works. 

By the way I have exactly the wireless card that you mentioned (Atheros).

I tried to search for some solutions. No luck yet. In fact I don't want to break my system. Poor performance is better than nothing at all. Probably in the end I will have to try Windows 7. Hate to do this....but this is life

AJVS

---

### Post by ajvsouza on 2009-12-05
David,

I followed the instructions from you 1st post (running linux-backports-modules-wireless-karmic-generic). Unfortunately my "hardware driver" utility does not show anything beyond NVDIA drivers

Tks

AJVS

---

### Post by ajvsouza on 2009-12-05
I found some threads suggesting to disable power management for the wireless and it worked perfectely

sudo iwconfig wlan0 power off

I created a startup script, added to "startup applications" and everything is fine. Now I am able to watch my TV videos stored in my old machine :popcorn:

#!/bin/bash
echo "yourpassword" | sudo -s iwconfig wlan0 power off


Hopefully Ubuntu next release will fix this issue

---

