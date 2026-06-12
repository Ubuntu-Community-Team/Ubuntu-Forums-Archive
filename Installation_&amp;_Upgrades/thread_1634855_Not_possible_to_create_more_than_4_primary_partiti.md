---
title: "Not possible to create more than 4 primary partitions - Crunchbang"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2010-12-01
I'm trying to install Crunchbang on a partition I made. I managed to resize my Ubuntu for space to install Crunchbang (which essentially is another Linux OS). 

I currently have Ubuntu 10.10 and Win7 currently installed. The error I get in GParted is the one above in the title. I know there is a way to install a third OS but this problem is killing me. I need some to help my step-by-step. I'm not that bright when comes to technical terms and writing stuff in the terminal. :p

My current filing system:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4600c452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        2300    18432000   82  Linux swap / Solaris
/dev/sda3            2300        8906    53057536   83  Linux
/dev/sda4   *       15354       60802   365054976    7  HPFS/NTFS

---

### Post by Herman on 2010-12-01
We can't make more than four primary partitions.

We can make between zero and four primary partitions or up to three primary partitions plus one extended partition inside which we can create a whole string of logical partitions.

SO, you need to get rid of one of those primary partitions and create an extended partition.
The easiest one to get rid of will be your swap area, /dev/sda2, delete it.
If you boot a Live CD with GParted in it and delete it you will need to right-click on it and click 'swapoff' first, because the live cd will probably have automatically found it the started using it. Once you click 'swapoff' to tell the Live CD to leave it, you should be able to delete it okay.

After that, resize your Windows partition smaller, leaving enough space after it for whatever other operating system(s) you want to install.
Create an new 'extended' partition, which is something like an empty box for holding lots of logical partitions. Your extended partition should be as large as possible, filling up all of the free space. 
Inside your logical partition you can now make yourself a new swap area, and you'll now be able to make quite a large number of partitions beside it inside the extended.Now you can install all the operating systems you want.

You may want to edit the /etc/fstab file in Ubuntu to tell it the UUID number for your new swap area, that will help ensure your Ubuntu will keep working at its full speed.
You can use the command sudo blikd' for a list of partitions and their UUID numbers. 
You can open the /etc/fstab file with 'gksudo gedit /etc/fstab'.
Just copy the UUID number from your blkid output and paste it into your /etc/fstab file over the top of your old swap area's UUID, save and close the file. :)

---

### Post by lifelike27 on 2010-12-02
Alright, I think I've understood what has to be done. I'm not quite sure how EXACTLY to create an 'extended' partition, but I'll try to mess around.

P.S: I've already freed up some space from my Ubuntu partition (which doesn't show up here) so there wouldn't be any need to resize my Win7 partition.

---

### Post by Herman on 2010-12-02
> I'm not quite sure how EXACTLY to create an 'extended' partition, but I'll try to mess around.You right-click on the area of free space and click 'New', which is right at the top of the right-click menu. 
A 'Create New Partition' window will open, and it has a spinbox over towards the right titled 'Create as'. 
There are three choices, 'Primary', 'Logical', or 'Extended'.
I'm sure you'll find GParted quite straightforward and easy to use once you get started with it.

It doesn't really matter which partition you resize to get the free space. It's just that your Windows 7 partition is relatively large.

---

