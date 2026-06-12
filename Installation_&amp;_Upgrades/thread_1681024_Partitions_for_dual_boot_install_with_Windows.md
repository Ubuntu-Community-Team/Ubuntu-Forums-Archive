---
title: "Partitions for dual boot install with Windows"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2011-02-03
Following is the layout of the current partitions of my single hard drive viewed from Windows 7:
[IMG]http://i.imgur.com/LEolw.png[/IMG]

As the figure shows, my current partitions are:
 - C: has Windows 7 system files and my personal data;
 - Q: for Lenovo recovery;
 - SYSTEM_DRV: for Windows boot files;

My goals are:
 - to create another partition D: for my personal data, and dedicate C: for Windows system files and applications only.
 - to install Ubuntu alongside Windows. D: will be shared between the two OSes, and home of Ubuntu will not be served as the primary storage place for my data, and just for some current programming projects.

 
I know I have to shrink C:. But I was wondering
 - Could you design a reasonable plan for my partition case? Specifically, for each partition, how much size, and primary or logical? Can you give a rough description of what steps shall I do within Windows 7, and what steps to do when I restart into Ubuntu installation CD?
 - Shall I defragment the hard drive before the process starts? I was also wondering if and when I shall check the hard drive and file system for errors?
 - My current C: partition has already been occupied with around 86 GB. If I want to shrink C: for storing Windows 7 system files and applications to a smaller size , such as 50 GB, shall I move out some files on C: to drop its occupied size below 50 GB before I am able to shrink C: to 50 GB in Windows 7?

Thanks and regards!

---

### Post by oldfred on 2011-02-03
Use windows tools for windows and Linux tools for Linux. Or use win7 to shrink the win7 partition. NTFS partitions need about 20 or 30% extra space to work well, so do not try to shrink too much. Defragging does not hurt. Besure to have good backups before installing. Check that windows boots after shrinking as it will at least want to run chkdsk.

I prefer the separate NTFS data partition for any data you want to share with Ubuntu. I do not recommend directly writing into another system's system partition unless you have to make repairs.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by flylehe on 2011-02-03
Thanks, fred!

   1. Is it correct that the free space generated from shrinking C: will only be able to create an extended partition, since there are already 3 primary partitions? So must D: be one logical partition on the extended partition, just as the partitions for Ubuntu will be? Will this be bad sometime? If yes, other better solutions?

   2. What are the good utilities to accomplish the partition tasks? Can Ubuntu installer solely handle them? Or better to have some of the jobs done in Windows with some recommended softwares?

Thanks and regards!

---

### Post by oldfred on 2011-02-03
I use gparted which is part of the Ubuntu liveCD. But I have also download the very newest gparted which is a liveCd of its own. Do not use windows to create partitions as it will just go ahead and create more than 5 but convert to dynamic or SFS partitions that are not compatible. Windows uses logical partitions in the extended without problem, but it cannot directly boot from a logical.

 [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

the installer will let you create Linux partitions, it did not let you create the NTFS partitions before but it is using gparted to handle the partitioning. I always prefer to partition in advance. You also can partition and then reboot windows to make sure it still is ok before installing Ubuntu/grub and overwriting the MBR. Minimizes any issues with windows booting after install.

---

