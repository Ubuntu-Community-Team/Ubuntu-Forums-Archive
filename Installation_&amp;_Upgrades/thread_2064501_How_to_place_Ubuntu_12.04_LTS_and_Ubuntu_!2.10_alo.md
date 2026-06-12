---
title: "How to place Ubuntu 12.04 LTS and Ubuntu !2.10 alongside preinstalled Windows 7?"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by resander on 2012-09-29
The preinstalled Windows 7 spanned the whole disk when the PC came so I made it smaller by using the Windows 7 Disk Manager. Unfortunately, Windows did not let me shrink the Windows partitions below about 240GB. I installed Ubuntu 12.04 LTS using the rest of the space on the 500gb hard disk just to try it. The attached image shows the Windows and Ubuntu partitions.

I have finished experimenting and would like to have two Ubuntus sharing the remaining disk space in the extended partition, Ubuntu 12.04 LTS and a more recent Ubuntu (12.10, 13.04...betas appearing during the lifetime of 12.04 LTS - initially it would be 12.10 beta).  

I would like the home directory of 12.04 to be shared by 12.10 and the swap partition to be shared too since only one Ubuntu is active at a time. 

How can I do this? Especially how do I specify the mount points?

---

### Post by darkod on 2012-09-29
Use the manual partitioning option during install and you can specify which partition to be used as what (filesystem, mount point).
If you want to use already existing partition, select it and click the Change button below.

Sharing /home between two different versions is a bad idea, especially if one of them is beta/alpha. There will be programs with different versions, and the settings kept in /home will clash.

The swap partition can be used between them, no problems, since you will only have one booted at the same time.

---

### Post by oldfred on 2012-09-29
+1 on Darko's comments.

I have not resized a Windows 7, but saved this info:
Resize Vista partition, similar for 7
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC.
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS.

I prefer to create shared data partition and leave /home inside the / (root) partition. I am aggressive about moving data from /home and my /home is 2GB with over 1GB of that as .wine which is the only larger data that I do not move.

I have  a shared NTFS data partition for any data I wanted to shared with my XP install, and still have it even though not booting XP. I put all new data in a /mnt/data partition for sharing with my various Ubuntu installs.

As long as you do not hibernate nor encrypt /home you can share swaps.

---

