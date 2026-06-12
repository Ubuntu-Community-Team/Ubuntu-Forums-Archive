---
title: "Would I Have A Problem Mounting a 6.06 Drive After Install?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by bper on 2007-10-19
Hi,

I have 2 SATA 250 GB drives that I've been using with my 6.06 64bit installation. The second disk is a partition that I used for data storage, and now that I plan to do a fresh install of 7.10, I've backed up some data onto that disk as well.

If I do a fresh install of 7.10 onto disk1 without changing anything on disk2, will I have any issues mounting, accessing, reading my data on disk2 after the 7.10 install?

What is the best way to safeguard or to perform this upgrade?

Thanks.

---

### Post by louieb on 2007-10-19
What i'm doing right now is running parted from the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and backing up my Feisty install to my data partition. (separate hard drive too).  If your doing a fresh install of Gutsy over the 6.06 install just select the **manual partition option** and tell it to format and install on the 6.06 install partition. 

Shouldn't have any problem with 7.10 seeing and using the partitions on your second drive.

---

