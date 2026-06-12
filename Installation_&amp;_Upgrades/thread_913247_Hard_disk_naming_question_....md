---
title: "Hard disk naming question ..."
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by gpsmikey on 2008-09-07
Greetings all -- could not find the answer to this under the
rocks I looked under.  Installed Hardy Heron from the LiveCD
onto a spare system with a ASUS P4T-E motherboard.  Hard drive
(200 gig IDE) is off the main controller on the motherboard.
All went well EXCEPT, from what I have been reading, IDE hard
drives are hda? etc -- all partitions on this drive are listed
as sda2 - extended (which contains sda5 - the ext3 file system
and sda6, the swap partiton).  The sda5 and 6 make sense as
they are inside an extended partiton, but why isn't the drive
labeled as hda instead of sda ???  Seems to work fine, but
I am curious (sd1 has BING from Terabyteunlimited - boot mgr
loaded in it).  Inquiring minds want to know !! :)

mikey

---

### Post by mikewhatever on 2008-09-07
As of Feisty Fawn (Ubuntu 7.04) all drives are labeled sdX.

---

### Post by doas777 on 2008-09-07
> **gpsmikey said:**
> Greetings all -- could not find the answer to this under the
rocks I looked under.  Installed Hardy Heron from the LiveCD
onto a spare system with a ASUS P4T-E motherboard.  Hard drive
(200 gig IDE) is off the main controller on the motherboard.
All went well EXCEPT, from what I have been reading, IDE hard
drives are hda? etc -- all partitions on this drive are listed
as sda2 - extended (which contains sda5 - the ext3 file system
and sda6, the swap partiton).  The sda5 and 6 make sense as
they are inside an extended partiton, but why isn't the drive
labeled as hda instead of sda ???  Seems to work fine, but
I am curious (sd1 has BING from Terabyteunlimited - boot mgr
loaded in it).  Inquiring minds want to know !! :)

mikey


I was always told that sda was for serial hdd types like scsi and sata.
hda is for IDE bus types.

It may be they started using sda, because sata is rather prevelant these days, and by using a single prefix you can reduce confusion, and provide more consistent support with fewer questions.

---

### Post by mikewhatever on 2008-09-07
You guys can read more on this topic here [http://ubuntuforums.org/showthread.php?t=422336](http://ubuntuforums.org/showthread.php?t=422336)

---

### Post by doas777 on 2008-09-07
> **mikewhatever said:**
> You guys can read more on this topic here [http://ubuntuforums.org/showthread.php?t=422336](http://ubuntuforums.org/showthread.php?t=422336)

ahh, so the kernel team is deprecating the old driver. that makes sense.

thanks

---

### Post by _Fred_ on 2008-09-07
my deb unstable system failed to boot a few months ago when i went from 2.6.22? to 2.6.24. It would be nice if you got some warning when installing a later version while running a newer version "fix your fstab and menu.lst or it wont boot noob" or similar ;-)

Those are the hazards of running unstable though.

---

### Post by gpsmikey on 2008-09-07
> **mikewhatever said:**
> You guys can read more on this topic here [http://ubuntuforums.org/showthread.php?t=422336](http://ubuntuforums.org/showthread.php?t=422336)


Ah, ok, thanks -- I had been reading up on this in such docs as "Partitioning your disks" [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html) where it specifically stated that "The first Master IDE hard disk is called hda" and in the "Partitioning Basics" in a forum tutorial style post at [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) where both clearly indicated hdx was IDE and sdx was scsi (although a number of controller cards show up as SCSI).  Granted the tutorial post was from 2006, but the "Partitioning disks" was from the 8.04 docs so I was confused (not an unusual situation actually :lolflag: )

Thanks for the info - I do try to RTFM even if it is wrong !!

mikey

---

