---
title: "Triple Boot Install Problem"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by badogg on 2007-12-02
Hi All....

Ok, I am having a problem during the partitioning section of the install of 7.10 Gutsy.  I have 3 SATA hard drives.  SATA1 and SATA2 are setup in a nVidia striped RAID array (Asus P5N-E Sli 650i board), and SATA3 is outside of the array as just a stand alone drive.  So I have several partitions within the RAID array, one of which has Vista on it, and a couple of other partitions for other functions for organizational purposes and such.  For SATA3 drive, I have a portion of the drive partitioned and have Windows XP Pro installed in it (It was easier than trying to get it installed into the RAID array during the XP install.  the remaining space is unpartitioned (approx 192GB) and I would like to use that for Ubuntu.  The problem I have is there doesn't seem to be any way to have the partitioner during the Gutsy install do an automatic partition setup of this unallocated space, and I don't know enough about what needs to be setup to do it manually.  So just looking for a little advice if ya'll don't mind.

Hope that made sense, I tried to be as descriptive as possible...

Thanks a lot!!

---

### Post by badogg on 2007-12-03
Anyone?

---

### Post by louieb on 2007-12-03
I got a big mouth. But I don't have any experience with raid. But you say sata3  isn't a part of the  raid array. 
Just a couple of things you might look at. I take you have the live CD might take a look at  GParted (System>Administration>Partition Editor)   see if you can make a sense out of it. As long as you say away from the apply button it won't do any thing. 
And here a couple of links about using GParted and Dual Booting.
 [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

