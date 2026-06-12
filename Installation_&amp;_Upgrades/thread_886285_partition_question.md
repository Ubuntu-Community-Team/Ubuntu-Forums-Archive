---
title: "partition question"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by tontopainter on 2008-08-11
I am completely new to Linux.  I saw it for the first time today and decided to try it out.  I have a brand new installation of windows xp on a 40 gig hd.  I told it to contain only 1 partition.  I ran the live cd and was in the process of going through all the questions etc.  I got through the partition portion of the installation, decided to give windows 20gb and ubuntu the remaining 18+ gbs.  Well when i was reviewing the data before the final install I realized I had to change something, and I went back to the city question.  Now it is trying to install both windows and ubuntu in a 20gb partition.  How do I change this back to 20gb for windows and 18 for Ubuntu?

---

### Post by castor_troy on 2008-08-11
First of all i  would like to know whether the 18+ gb partition has already been created. It seems as though it has been because it is trying to install both ubuntu and windows on 20gb parttion.

If you can confirm this then solving the problem would be easier.

Cheers !

---

### Post by mikewhatever on 2008-08-11
If you only saw Ubuntu today for the first time, what's the rush to install it? Run it from CD for a couple of days, see if you like it.
To help you with partitions, some more info is needed. While in the live CD, open Applications>Accessories>Terminal, type **sudo fdisk -l** (small L, not number one) and post the output.

---

### Post by SkonesMickLoud on 2008-08-11
Since you're so new to Ubuntu and Linux, you might want to play around on the CD for a little while.  Just remember that the CD will run much slower than a fully installed system.

That said, it may be worthwhile for you to check out [Wubi]("http://wubi-installer.org/") first.  It let's you install and uninstall Ubuntu as if it were a Windows program.

---

### Post by tontopainter on 2008-08-11
> **castor_troy said:**
> First of all i  would like to know whether the 18+ gb partition has already been created. It seems as though it has been because it is trying to install both ubuntu and windows on 20gb parttion.

If you can confirm this then solving the problem would be easier.

Cheers !

Well I went ahead and installed it on the 20 with windows to get it on and to check it out.  I chose to go ahead and install it without playing with the live cd much, because I had no reason not to....My roomate trashed my windows installation so I was starting this box back up from scratch.  I guess my question now, is can I take the additional 18+ gbs of hd and combine it with the other two partitions? (which now hold xp and ubuntu)

---

### Post by ramnarayan on 2008-08-11
> **tontopainter said:**
> My roomate trashed my windows installation so I was starting this box back up from scratch.  I guess my question now, is can I take the additional 18+ gbs of hd and combine it with the other two partitions? (which now hold xp and ubuntu)

No problem - the less space for Wincedows the better ;-)

ok in terminal run
df -hT

post it here.

Of course you can use the remaining space easily 
if you want to share it between wincedows and ubuntu then use the partition editor to format it as vfat (fat32) and give it a nice name. It will be accessible from both.

ram

---

