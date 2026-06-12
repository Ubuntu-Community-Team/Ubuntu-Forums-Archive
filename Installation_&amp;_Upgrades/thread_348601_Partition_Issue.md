---
title: "Partition Issue"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by Zander_Z on 2007-01-29
Here's the deal. I'm running off of a Ubuntu Live CD 6.06 Edgy. I choose install, and it runs fine all the way up to partitioning. It pulls up Gparted and shows me I have a /dev/sda1 NTFS partition of 157.76 unused GiB an unallocated of a few megs, and then a /dev/sda2 fat 32 (windows uses that as it's recovery space) of approx 9 GiB.

 I split the NTFS into three, a linux-swap of 4 GiB (double my RAM) and a ext3 partition of 10 GiB for the / (root). I also leave what's rest for a /home directory for updates. Great right? ...No. I click the "Apply" button and it gives tells me it can't do any of the above tasks. It says "check filesystem on /dev/sda1 for errors and (if possible) fix them"

I'm trying to set up a dual boot system so that I can continue to use Windows XP off and on.

Does anyone have any ideas on why I can't partition?

---

### Post by lnc on 2007-01-29
A few days ago, when i installed ubuntu i had the same problem.
I don't know why, but when i used Magic partition Pro 8 for this task:
- Create new partition for root
- Created a new partition for swap

After that i reinstall Ubuntu, It is OK.

---

### Post by Zander_Z on 2007-01-29
So, do I download and use the trial version of partition magic 8.0 in windows and use that to create my partitions for Ubuntu to use? Or is there another way I could possibly set up partitions using different freeware / software? 

-Any help is appreciated, thanks Inc for the info! :D

---

### Post by housam on 2007-01-29
Y ou already have 2 primary partitions  (157 & 9 Gb) and you only able to create 4 primary partitions on a single HDD. If you need more partitions , you have to convert one of the primary partitions to an extended partition which can be devided to any number of partitions you want.
Please note that partition magic is not the suitable tool for partitioning for ubuntu. use the Gparted to do the job, it is perfect for ntfs and ext3 format.
Do the defrag at least twice before resizing your xp partition and back-up every thing. create all your partitions manually before installing ubuntu, that put every thing under control. here is an example:
Resize the windows to create an unallocated space of about 41Gb ( or what ever you like )
Now devide the unallocated space to two new partitions:
-10 Gb ext3 for the root ( / ) as primary partition
-31 Gb as EXTENDED PARTITION
Devide the extended partition to 2 new logical partitions
-1 Gb swap for the ( swap )
-30 Gb ext3 partition as /home 
After that go for the installation and when it comes to the partition mater , choose the manual way .

---

