---
title: "Ubuntu 7.04 killed my Inspiron 8600's hard drive"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by klhammond on 2007-11-08
So, last night I decided to install Ubuntu 7.04 onto my Dell Inspiron 8600 over an existing Red Hat installation.  I have triple booted XP, QNX and Red Hat on the machine for almost 4 years and have had no problems.

I put Ubuntu inside the extended partion, since all the primary partitions were taken.  It was an 8gig partition at the end of the drive, mounted as "/".  The install went smoothly and even went through the 135 updates that were available.  I rebooted and it was a go.

I tried to open Firefox and it did not want to open, then the hard drive started making clicking noises and the system hung.

Now, whenever I start up the computer, the clicking is still there and the BIOS does not see the HD at all.  I do not think it is a random HD failure, but unsure as how to fix it, other than replacing the HD.

---

### Post by dabl on 2007-11-08
Maybe not exactly "random", in the sense of a light bulb burning out, but did you ever notice that light bulbs only burn out when you switch them on?

Installing an OS is a pretty disk-intensive activity, compared to just running a system.  After 4 years of daily use, depending on how you normally used it, it is not difficult to imagine that your hard drive may have been "ready to die" upon being pushed really hard.  Hard to say for sure -- newer hard drives are pretty reliable, but they are, at heart, mechanical devices subject to wearing out.

---

### Post by waffen on 2007-11-08
Uhm.... Ill the same error in my Latitude, with a 2 years Seagate HD... 

Please: buy a new HD! :(

---

### Post by unixcrab on 2007-11-08
Any of you seen this?
[http://hardware.slashdot.org/article.pl?sid=07/10/30/1742258](http://hardware.slashdot.org/article.pl?sid=07/10/30/1742258)

---

### Post by klhammond on 2007-11-08
I did read about that, and the steps to reduce it.  My problem occured immediately after installing and simply starting Firefox.  

I blame Firefox!

I can get a new HD, and I have backups, I just really dont want to go through the hassle of reinstalling everything.

---

### Post by klhammond on 2007-11-08
I pulled the drive out and it is a Hitachi TravelStar 60gb, 7200rpm drive.  I found some diagnostic tools at 

[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

I booted from the CD and ran the Drive Fitness Test.

Looks like I had a spectacular drive failure, just when I needed it least.

---

