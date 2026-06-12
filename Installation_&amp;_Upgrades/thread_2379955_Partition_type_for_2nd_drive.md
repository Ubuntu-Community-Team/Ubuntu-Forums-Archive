---
title: "Partition type for 2nd drive"
date: 2017-12-11
forum: Installation &amp; Upgrades
---

### Post by mikenh on 2017-12-11
Just completed a new build with two SSD's and I'm starting an install of Ubuntu 16.04.  Drive one (sda) for / and swap and /home and the 2nd drive (sdb) for backups of /home, and future warehouse storage of photos and videos. In trying to create a partition for backups on sdb none of the mount points seem suitable since I can't have two /home partitions. Which to choose? /usr/local or /var or is there another choice?

---

### Post by oldfred on 2017-12-11
I now only use gpt for partitioning whether BIOS or UEFI.
And I use /mnt/data for all my data on HDD but boot from SSD. And link folders back into /home.
If you use /media then it will show just as one entry in Nautilus.
I keep /home as folder inside / (root) as all data is in data partition.

I primarily started using data partition(s) as I was dual booting. Originally XP & Ubuntu, then other flavors of Ubuntu more as tests. But wanted all data in all installs.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by mikenh on 2017-12-11
Thanks OldFred, but sorry to say but your post is mostly over my newbie but old head. I'm using the manual partitioning on the Installation disc, so there's no /mnt nor /media option, for example. Do I even need to partition the 2nd SSD at this point? Can I mount it later w/o partitioning and use a directory structure to separate and organize files?

---

### Post by yancek on 2017-12-11
When you use the Something Else 'manual' option and click on free/unallocated space on the second drive (sdb) and then click on the plus + in the lower left of the window you should get a new Edit partition window.  On that window you will have an option for Mount point and you can click the drop down arrow and enter whatever you want; /mnt/data as an example.  You can leave this and just do the install and then after the installation, you should be able to use the gparted partition manager from the installed Ubuntu to create partitions and mount points for backups or whatever you want.  A sample of the edit partition window is on the page at the link below, scroll about half way down.

[http://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-ubuntu-16-04-with-screenshots.html](http://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-ubuntu-16-04-with-screenshots.html)

---

### Post by oldfred on 2017-12-11
Best to partition, those that use drive unpartitioned often have issue. Most tools expect partitions. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

More info on partitioning.
 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions old BIOS info:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) 

If you use Linux format you will have to give yourself ownership & permissions to read/write into it.
You /home if a separate partition,  is automatically set with ownership & permissions. And mounted in fstab for your use.

---

### Post by mikenh on 2017-12-12
Thank you, Yancek, that's exactly what I needed. I just didn't perceive that I could enter a path in the box, nor could I find a comparable partition recommendation among all the dual-boot scenarios.

---

