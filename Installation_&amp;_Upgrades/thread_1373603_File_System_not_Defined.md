---
title: "File System not Defined"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by D!cK0 on 2010-01-05
Hi folks,

Complete Newbie here.  I'm trying to install Ubuntu build 9.10 on my Macbook Pro.  All's fine and and dandy when it comes to partitioning the hard drive on Boot Camp.

However, when installing Ubuntu I get to the Partitioning stage (Step 5 I believe) and when I select the space that I have allocated for Ubuntu (80g) and go to hit forward, the wizard hits me with File System not Defined. 

Question is to you guys, do I then have to select that space and edit it with the Change function (if so what do I change), or,  do I have to change the way the space is formatted on the OSX side of things.

The partitioned space is hfs if that has anything to do with it?

Running OSX 10.5.8 all up to date.

---

### Post by zvacet on 2010-01-07
Define filesystem as ext4 and let that partition be root / .If you want to have separate home partition see [this.]("http://www.psychocats.net/ubuntu/installseparatehome") it is good thing to make separate home,because you can do reinstal.fresh install... and your setting will be safe.

---

### Post by D!cK0 on 2010-01-08
Cheers mate, I got it sorted anyways with a bit of fiddling about.

Full Ubuntu now :D

---

