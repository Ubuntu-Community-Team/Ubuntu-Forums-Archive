---
title: "[SOLVED] Install 8.10 over 8.04 on multi-partitioned HDD?"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Eric Qel-Droma on 2008-11-13
I currently have three partitions on my drive:  one NTFS, one Ubuntu 8.04, one straight FAT32.  Is it possible to do a fresh install of 8.10 OVER the 8.04 and leave the other two partitions untouched?  I'm not much of an installation guy, so if there are going to be any weirdnesses or even the possibility of such, I'd rather wait.

Thanks in advance,

Eric

---

### Post by lswb on 2008-11-13
If by "fresh install" you mean to do a clean install of 8.10 into the partition formerly used by 8.04, then boot the 8.10 live CD, and use gparted to delete the 8.04 partition on your hard drive. Then do the 8.10 install. Carefully check the partition options, normally it will give you a choice of partitions to install in, just select the one that had 8.04 and leave the others alone.

If you meant to upgrade the 8.04 system to 8.10, then follow the upgrade instructions.

In either case, it is recommended to backup the partitions you want to keep.

---

### Post by Eric Qel-Droma on 2008-11-13
So I have to do 8.10 live, run something called "gparted" (which I assume is just a partition utility included in 8.10 live) and *delete* the current 8.04 partition?  Will that leave the space unformatted until I reformat it?  

(I don't know what it specifically means to "delete" a partition as opposed to simply removing all files or reformatting the partition.  I'm also surprised that I can't do the partition deletion during the actual installation.)

Sorry if all that sounds stupid on my part--I'm just trying to restate what you said to make sure that I understand you.  Thank you very much for the quick response!

Eric

---

### Post by lswb on 2008-11-14
Deleting the partition just means marking it as "unused" And I didn't mean to imply that you _had_ to delete it prior to installation.

gparted is a partitioning program that creates, deletes, resizes, and copies disk partitions and installs filesystems (formats) on them.

You don't have to actually delete the partition first. I don't have an install disk handy to check what the exact steps are, but you can just tell the installer to use an existing partition. Deleting it first will just make it a little more obvious which one you want to use. The installer will run gparted anyway during the install process. 

You can run the installer up to the point of selecting the partition(s) you want to use, and can cancel or change things until you actually write the new partition info and data to the disk. Before you write to an existing partition with data on it, you will get the usual warnings about old data being overwritten.

---

### Post by Eric Qel-Droma on 2008-11-14
Thanks again.  Very helpful!

---

