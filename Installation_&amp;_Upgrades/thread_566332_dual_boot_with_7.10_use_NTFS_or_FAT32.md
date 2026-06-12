---
title: "dual boot with 7.10 use NTFS or FAT32?"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by sagesparrow on 2007-10-03
I posted this on Absolute Beginner forum with no responses, so maybe I'll have better luck here.

I am just getting ready to set up a dual boot system with XP Pro and Ubuntu. The plan is to have at least one separate partition for files, email boxes, etc. that will be shared by both XP and Ubuntu. This was going to be FAT32. But should I set it up as NTFS in anticipation of using Ubuntu 7.10 (instead of Feisty) which is supposed to have read/write capability with NTFS? Or just go with FAT32? What are advantages of each? 

Also, does having files on separate partition affect the performance/speed of accessing files?

Thanks

---

### Post by wolfen69 on 2007-10-03
this might help you decide [http://thundercloud.net/information-avenue/ntfs-vs-fat32/](http://thundercloud.net/information-avenue/ntfs-vs-fat32/)

---

### Post by dabl on 2007-10-03
With the ntfs-3g package (available in the repos), *buntu has no problem reading and writing to a NTFS format partition.  NTFS is a more reliable filesystem that FAT, wrt crash recovery, so that kinda turns it into a no-brainer.  :)

---

### Post by rsambuca on 2007-10-03
I would personally use (and do use, actually!) the ext3 filesystem for your shared partition.  You can then just install the [fs-driver for Windows]("http://www.fs-driver.org/") so that you have full read/write access from Windows.  The ext3 filesystem is superior to ntfs, which is vastly superior to FAT32.

---

