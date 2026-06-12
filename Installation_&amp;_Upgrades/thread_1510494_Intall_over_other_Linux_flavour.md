---
title: "Intall over other Linux flavour"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2010-06-15
I am running a dual boot Win XP and OpenSUSE 11.2. I would like to replace openSUSE with the latest version of Ubuntu. Is there an easy way to do this?

---

### Post by ajgreeny on 2010-06-15
Use the live CD, double click the install icon on the desktop, then when you get to the partitioning part, choose manual partitioning and you can just choose the partitions you already have Suse installed on as the partitions for Ubuntu.

As you are manually installing anyway, it is worth using a separate /home partition.  See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by new_tolinux on 2010-06-15
Another way is to delete the OpenSuse partitions within XP and then boot the Ubuntu cd.
Choose to use the largest free space, _not_ the option to use the whole disk.

---

### Post by vchapman on 2010-06-16
Here is what I have
/dev/sdb
/dev/sdb1 fat32 78741
/dev/sdb5 swap 1595
/dev/sdb6 ext3 15695
/dev/sdb7 ext3 21047
free 5667

I want to keep most if not all of the fat32 partition. How should I proceed with the Ubuntu install?

---

### Post by Yarui on 2010-06-16
It depends on how exactly you want your partitions set up.

If you want them to be the same as your SUSE setup, then do it the way greeny suggested.  Just run the install and when you get to the partitioning step where it asks if you want to install on the whole disk or if you want the disk to be part windows and part ubuntu select the custom method and then just select the partitions that are already there to install to, leaving the fat32 partition alone.

If you want to set up your partitions differently, though, delete the SUSE partitions and then set up your ubuntu partitions in the free space.

---

### Post by vchapman on 2010-06-16
> **ajgreeny said:**
> Use the live CD, double click the install icon on the desktop, then when you get to the partitioning part, choose manual partitioning and you can just choose the partitions you already have Suse installed on as the partitions for Ubuntu.

As you are manually installing anyway, it is worth using a separate /home partition.  See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I have 50 gb of disk space for the install. All of my pictures, music and data files are maintained outside of the space required for the Ubuntu install.

I would like to assign 4 gb to the swap file (although I have read this may not be necessary)

If I have 45 gb of space how much do I assign to 
/
/home

---

### Post by Yarui on 2010-06-16
The general guideline I have seen for swap space is twice the size of the amount of memory you have, if you have room for that much.  The reason for this is that if you hibernate your machine everything in your memory is put into your swap space, I believe.  So if you have a large percentage of your memory used up and have some stuff already in the swap space, it's good to have enough space for all of that.  You probably won't ever need that much, though, so if you would prefer less it is perfectly acceptable to set it equal to the amount of memory you have.

The amount you allocate to your home and root partitions is really up to you.  I personally never separate those two because I don't want to put a capacity limit on either one.  I just back up my home folder before a format instead of keeping my home folder on a separate partition.  If you are the only user on your computer, the separate partition for your home folder isn't really necessary.  It is really all about preference.

Some people do things on separate partitions for security reasons, but you just have to decide whether or not you really need to be that cautious.  I don't find it necessary for my own needs.

---

