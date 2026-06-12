---
title: "increasing Ubuntu partition using palimsest"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by tesko on 2009-12-06
I have ubuntu netbook remix 9.10 installed and would like to increase its partition and minimize windows one.  I'd still keep windows just in case but keep HD  space there to minimujm.  I  am not sure how to go about it.  I see palimsest disk utility tool but am afraid to mess with it.  any directions on how to accomplish increasing ubuntu partition?

This is what I see when I open palimsest on Lenovo S10

-160 gb Hard disk
-87 gb file system FAT 32 bit version
-57 GB extended contains logical partition
--Lenovo 33GB NTSF
--23 GB files system Linux Ext4 version 1
--1.1 GB swap space
-16GB Files system NTFS

I think 87 GB is where my files are on windows.  I'd like to back am up and make this part of linux partition.  Also if I can get rid of 16GB NTFS Id like that too ( I think it is vista loader or something like that) alond with Lenovo 33GB NTSF which is their one recover system.

Is this possible w/o fresh reinstall?  please let me know.

---

### Post by georgeen on 2009-12-11
Well I'm not an authority in this topic and I don't use palimsest for that kind of shores (excuse my english if any please), for that I use GParted. I recomend that before do anything do a backup, and have a list of windows controllers and if you can, their software. If you have Win7 installed I don´t recomend Gparted and I don´t know if with palimsest doesn't give you problems. The basic steps are

**1)** Backing up your work on both operating systems
**2)** Defrag in Windows
**3)** Go to Linux and with GParted resize the windows partition (shrink it), be very careful to leave space between your last data (last in disk position not in date) and the limit that you are defining to avoid data lost in Windows.
**4)** Move the NTFS recovery partition if is necessary to be side by side with Windows partition
**5)** Move your Linux partition to be side by side with your recovery partition
**6)** Resize the linux partition (grow the size) until you need or want
**7)** Apply changes in GParted

This kind of operations are very risky and unusual to be honest but recently I have to move partitions from one disk to another in Ubuntu and was a big success only with GParted, and I have to do resizing and moves but I had the advantage that the data was little compared to partition size, so I have some fredom degree to resize.

I hope this help you.

---

