---
title: "I cannot boot into Windows after Ubuntu 10.10 install"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by andyboy on 2010-12-16
Hi ,
I had Windows 7 installed on a 640GB Hard Drive and was using Wubi to try out Ubuntu , I tried to install Ubuntu as a dual boot option but I am now unable to boot into Windows .

The output of sudo fdisk -l is 

#Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        1405    11204608    7  HPFS/NTFS
/dev/sda3            1405        8077    53587098    7  HPFS/NTFS
/dev/sda4            8077       77826   560258049    5  Extended
/dev/sda5            8077       75531   541827072   83  Linux
/dev/sda6           75531       77826    18429952   82  Linux swap / Solaris#

and the output of sudo parted/sda/dev/print is

#Model: ATA WDC WD6400AAKS-7 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  82.3MB  82.2MB  primary   fat16           diag
 2      82.8MB  11.6GB  11.5GB  primary   ntfs            boot
 3      11.6GB  66.4GB  54.9GB  primary   ntfs
 4      66.4GB  640GB   574GB   extended
 5      66.4GB  621GB   555GB   logical   ext4
 6      621GB   640GB   18.9GB  logical   linux-swap(v1)#

Any help would be greatly appreciated 

Thanks

---

### Post by Mark Phelps on 2010-12-16
I'm guessing you did NOT do the following:
1) Use the Win7 Disk Management utility to shrink the Win7 OS partition
2) Use the Win7 Backup feature to create and burn a Win7 Repair CD.

Right?

So now, since you most probably allowed the installer to shrink the Win7 OS partition, it's also probably corrupted the filesystem in the process.  You will have to repair that.

If you had gone to the trouble of burning the Win7 Repair CD, you would be in good shape.  But since you didn't mention that, you will have to go to the link below, download and burn a Win7 Repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot into that CD and run Startup Repair three times -- that's right, three times.  

That should repair your Win7 OS partition so it boots again.

---

### Post by andyboy on 2010-12-16
Hi ,

I did shrink the Windows partition but did not create the rescue disks 

I will do that now

Thanks for your help

---

### Post by aeroaishik on 2010-12-16
[CENTER][LEFT][CENTER]If you have the Windows installation disks then you can repair Windows. :popcorn: Now lets have a look at my ***[FONT=Arial]sudo fdisk -l[/FONT]***
[/CENTER]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf0b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9347    75078656   83  Linux
/dev/sda2            9348        9730     3069953    5  Extended
/dev/sda5            9348        9730     3069952   82  Linux swap / Solaris
[/LEFT]


I didn't have any problem after installing Ubuntu as I have totally changed from Windows. :D

**[SIZE=3]And if none of the solutions work then install a fresh copy of Windows and install Ubuntu in Windows with software like Virtual Box.[/SIZE]** :KS
[/CENTER]

---

### Post by andyboy on 2010-12-16
Thanks

---

