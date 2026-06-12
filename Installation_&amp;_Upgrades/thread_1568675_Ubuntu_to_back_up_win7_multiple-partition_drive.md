---
title: "Ubuntu to back up win7 multiple-partition drive?"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2010-09-05
I am looking for a good solution to back up a windows 7 system drive (2 partitions) after booting up ubuntu.  It should be good enough that if the drive dies, I can just put the image on a new drive and boot it up again.  Because only 20% of the drive is used now, dd (followed by bzip2) does not seem like not a good idea---although it might be if I zero out all unused sectors.  Not a great plan, though.

I love gnu tar, but I wonder if it is robust enough with the ntfs fs driver in ubuntu to save and restore all the auxiliary file system meta info that win7 is using on it's system partitions.  Do they still have sectors that have to be in a specific location?

What do you use?

Advice appreciated.

Iaw

---

