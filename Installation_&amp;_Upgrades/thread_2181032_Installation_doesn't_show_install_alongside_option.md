---
title: "Installation doesn't show install alongside option - only 2 primary partitions"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by John_Stein on 2013-10-15
I'm trying to install Ubuntu alongside Windows 7 but the option to install it alongside another OS doesn't appear even though there are only 2 primary partitions existent. There are 2 unallocated partitions but I don't think that can be the cause. What can I do to solve this?

---

### Post by dan-espinosa on 2013-10-16
What's in these partitions? Is it one physical hard drive? Please specify.
Did you format these partitions? If you're on Windows, delete the volume.
Right click on Computer, go to Manage, and select Manage Drives.

---

### Post by dan-espinosa on 2013-10-16
[http://www.youtube.com/watch?v=egO7VVeEtHw](http://www.youtube.com/watch?v=egO7VVeEtHw)

---

### Post by Bucky Ball on 2013-10-16
Delete the two empty partitions leaving free space and try again.

---

### Post by Mark Phelps on 2013-10-16
> There are 2 unallocated partitions  There's  no such thing as "unallocated partitions"; there is only unallocated space OUTSIDE partitions.  If this adds up to 4 partitions on your drive, that is the most you can have on an MBR-formatted drive.  The installer won't let you create any more partitions.

You should enter the following command in a terminal so we can see what you have: "sudo fdisk -lu" (lowercase L, not a one).

---

### Post by John_Stein on 2013-10-16
It's one physical hard drive with two primary partitions and 2 unallocated spaces labeled under logic. I'm using the MiniTool Partition Wizard because I only have an option to create a simple partition when using Computer Management, and I only have the option to wipe or create partition.

---

### Post by heir4c on 2013-10-16
If you boot Ubuntu with a usb or cd/dvd than you can use gParted (PartitionManager) to see the partitions and delete or create new ones. It is standard on any iso of ubuntu.

---

### Post by John_Stein on 2013-10-16
Using gParted is what got me the unallocated spaces I'm trying to delete, I can't delete them.

The results show as so:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc796c701

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       81920    17321983     8620032    7  HPFS/NTFS/exFAT
/dev/sda2        17321984  1953519615   968098816    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a4ca4cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    20595329    10297633+   7  HPFS/NTFS/exFAT
/dev/sdb2   *    20595330   976771119   478087895    7  HPFS/NTFS/exFAT

---

### Post by Bucky Ball on 2013-10-16
> **John_Stein said:**
> It's one physical hard drive with two primary partitions and 2 unallocated spaces labeled under logic. 

In that case why does the output report sda and sdb??? This indicates two physical hard drives, and all the partitions are NTFS.

You want FREE SPACE where you intend to install Ubuntu. DON'T create partitions for it using Windows or anything else. That will all be done when you install it.

As advised, boot from the Ubuntu install media, launch Gparted and delete the two partitions you don't want, leaving free space. Continue with the Ubuntu install to the free space.

The details of your TWO current drives are:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
/dev/sda1 * 81920 17321983 8620032 7 HPFS/NTFS/exFAT
/dev/sda2 17321984 1953519615 968098816 7 HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
/dev/sdb1 63 20595329 10297633+ 7 HPFS/NTFS/exFAT
/dev/sdb2 * 20595330 976771119 478087895 7 HPFS/NTFS/exFAT 
```

So, sda is a terrabyte drive and sdb is 500Gb. They have two partitions each. You appear to have sda1 and sdb2 set to boot for some reason.

---

### Post by John_Stein on 2013-10-16
I apologize, it was my fault for not being specific enough with it. The first hard drive, the 1 TB, is the one that I'm trying to create the Ubuntu Partition on, and it's the one that only has 2 primary partitions. The second hard drive is full and is being used for archived data, but from what I've gotten from my search, primary partitions from two seperate hard drives wouldn't affect the alongside installation would it?

---

### Post by Bucky Ball on 2013-10-16
> **John_Stein said:**
> ... primary partitions from two seperate hard drives wouldn't affect the alongside installation would it?

No. But you need to have free space to install to, regardless of where you're going to install.

---

### Post by John_Stein on 2013-10-16
Sorry I misunderstood, I have more than enough free space to install Ubuntu if that is what you're saying, I tried it again after freeing up some more space and it's still showing the alongside option

---

### Post by Bucky Ball on 2013-10-16
How do you want to install? Alongside Windows or ... ? Have you got the option 'Something Else'? That allows you to manually install and bypasses the alongside bit.

What I mean by free space is not NTFS partitions with nothing in them. I mean a space on the disk which has nothing on it and shows in Gparted as 'free space'. Not allocated and containing NO partitions at all.

---

### Post by heir4c on 2013-10-17
Give a screenshot of gParted, please, so we can see what you see. 

When looking at your partitiontable, there are 2 partitions on each HD. The sum of the partitions takes the hole HD. So where is the free space or unallocated space? Therefore we need the screenshot.

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc796c701

Device Boot Start End Blocks Id System
/dev/sda1 * 81920 17321983 8620032 7 HPFS/NTFS/exFAT
/dev/sda2 17321984 1953519615 968098816 7 HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a4ca4cd

Device Boot Start End Blocks Id System
/dev/sdb1 63 20595329 10297633+ 7 HPFS/NTFS/exFAT
/dev/sdb2 * 20595330 976771119 478087895 7 HPFS/NTFS/exFAT 


And give the output of:

```
sfdisk -l
```

---

### Post by John_Stein on 2013-10-17
Here is a screen of GParted.


I'm trying to install it on this physical drive, and sfdisk -l in terminal didnt' yield to any results

---

### Post by Bucky Ball on 2013-10-18
Well, you have nowhere to install it there. Boot into Windows, shrink the Windows partition (DO NOT do this in Gparted or Ubuntu) and leave some FREE SPACE somewhere. No partition, just free space. Boot from the Ubuntu install CD and install to the free space ...

Not sure how much clearer we can make this: You need free space to install Ubuntu to. How can you install alongside or anywhere else if there is nowhere to install Ubuntu???

---

### Post by John_Stein on 2013-10-18
Shrinking it just gets me a unallocated space just like I stated a page ago, it was one of the things I tried that didn't solve my problem. I shrunk 15 GB so there's more than enough free space to install alongside. I have 13.04 on the disk, could it be that I need 13.10 to do this?

---

### Post by heir4c on 2013-10-18
The 2 unallocated 'partitions' you mentioned are just a little bit free space about MB (and not GB). So you can ignored them. 
15GB is good but 20 or 25 is better (and think about the swap partition to).
But, I see there is only 50GB left on the Windows partition. That is too little, because Windows needs 20% free space to work well. So, backup a 50GB of the data on the window partition to a second (external) HD. And than you shrink the Windows partition with 25 GB for Ubuntu. If it is unallocated try to format it from Windows to fat32 or nfts, so gParted can see better the partition. Than you can change in the Ubuntu live-dvd/usb the partition in an Extended partition to make a / (root)partition and a swap partition.

---

### Post by heir4c on 2013-10-18
Sorry for: the command: sfdisk -l must be with sudo:
```
sudo sfdisk -l
```
(-l is a little L)

---

