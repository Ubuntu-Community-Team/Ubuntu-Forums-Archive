---
title: "How do I dual boot Ubuntu 6.10 and Windows XP pro?"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by cornflaker on 2007-01-30
Hey guy this is my first post,
I was wondering how I could dual boot Ubuntu 6.10 and Windows XP Professional.
I have Windows XP Professional installed onto a 300GB SATA hard drive and have another 250GB IDE hardrive connected currently formatted as NTFS (I plan to make this partition smaller to allow room for an EXT3 partition on which to put Ubuntu 6.10).
Is this possible? and how would I go about doing this if it is :confused:

---

### Post by bustanil on 2007-01-30
Try this one -> [http://ubuntuforums.org/showthread.php?t=346744](http://ubuntuforums.org/showthread.php?t=346744)

---

### Post by housam on 2007-01-30
Download and burn the 6.10 Edgy iso at the minimum burn speed i.e. 4x or 2x. to get a live CD.
back-up every thing. create all your partitions using the Gparted tool ( in the live CD)manually before installing ubuntu, that put every thing under control. here is an example:
Resize the partition to create an unallocated space of about 41Gb ( or what ever you like )
Now devide the unallocated space to two new partitions:
-10 Gb ext3 for the root ( / ) as primary partition
-31 Gb as EXTENDED PARTITION
Devide the extended partition to 2 new logical partitions
-1 Gb swap for the ( swap )
-30 Gb ext3 partition as /home 
After that go for the installation and when it comes to the partition mater , choose the manual way .

---

### Post by cornflaker on 2007-01-30
Thanks, I'll have a look at both of these.

---

### Post by cornflaker on 2007-01-30
> **housam said:**
> Download and burn the 6.10 Edgy iso at the minimum burn speed i.e. 4x or 2x. to get a live CD.


Hmm, Just curious, why burn it at the minimum burn speed?

---

### Post by housam on 2007-01-30
Just to avoid freezing during the install process due to burning corruptions. As you burn a complete system , fast burning sometimes corrupt the files.

---

### Post by cornflaker on 2007-02-03
Hmm, I think that may have happened to me, because when I installed it onto a separate hard drive earlier, the shutdown and reset buttons disappeared, I will burn a fresh copy and 8X, thanks or the info :)

Edit: It worked! thanks for the help guys :D

---

