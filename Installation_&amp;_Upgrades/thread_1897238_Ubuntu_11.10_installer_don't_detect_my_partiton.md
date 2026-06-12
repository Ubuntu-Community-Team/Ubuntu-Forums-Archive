---
title: "Ubuntu 11.10 installer don't detect my partiton ?"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by Gindro Rosetta on 2011-12-18
This problem started when i got a problem with busy box in ubuntu.

So,i installed windows XP SP3 in my PC. In progress, i divided my C: partition into 2. One is NTS format, and i'm forget to format the other one. 

After finish installation of windows XP3, i make usb installer of Linux and want to install it to my PC.

But in the middle of process, ubuntu installer doesn't detect my partitions. It only detect my HD as a partition.

So, i try boot live Linux and run the terminal and insert the code : sudo fdisk -lu, and here is the result

omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00e700e7

   Device       Boot               Start              End          Blocks        Id     System
/dev/sda1        *                  63     20482874       10241406         7      HPFS/NTFS/exFAT
/dev/sda2                    76173310      156280319    40053505          f      W95 Ext'd (LBA)
/dev/sda3             77818923      156280319       39230698+        7     HPFS/NTFS/exFAT
/dev/sda5             76173312        77817855        822272      82     Linux swap / Solaris

Disk /dev/sde: 3998 MB, 3998810112 bytes
124 heads, 62 sectors/track, 1015 cylinders, total 7810176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

Here is the screenshot :

[http://s10.postimage.org/8ip42ubcp/Partition.png](http://s10.postimage.org/8ip42ubcp/Partition.png)

I'm now stuck in Live Linux and can't do anything, because it won't detect my HD too, so i hope anybody wanna help me to fix my my problem. Any advices are precious for me

---

### Post by Buntumatic on 2011-12-18
From Ubuntu CD, delete all partitions, create one (sda1) for Windows, install Windows to this dedicated partition, run Ubuntu install again.

---

### Post by Gindro Rosetta on 2011-12-18
Yeh i have a same idea before, but i must save my precious files on my HD, so if i do that it will remove any files right ?

But thanks anyway for the ideas

---

### Post by Buntumatic on 2011-12-18
Well, then mount the partition with your files from liveCD and copy them over first, to a network drive or CDR/DVDR or whatever media you have available.

---

### Post by Gindro Rosetta on 2011-12-18
That's my last choice, 

And actually i have fixed my problem, using your #1 method, i'm somehow forget that i have 2 partition

I format C: into raw via windows XP CD, and run Linux CD to format it again into ext4

"VOILA" it's done

Sorry to bother you  
But, thanks bro, for the help you provide to me :lolflag:

---

