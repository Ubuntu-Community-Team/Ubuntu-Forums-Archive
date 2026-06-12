---
title: "Samsung ATIV 9 Lite"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by aridus on 2014-04-20
I have purchased a Samsung ATIV 9 Lite, which as a 128 GB SSD and Windows 8.1. I wish to install Ubuntu 14.04, removing Windows (there is insufficient hard disk space to run both well). I have read [http://help.ubuntu.com/community/UEFI](http://help.ubuntu.com/community/UEFI) but do not have a complete understanding of how to install Ubuntu without messing up the partitions. I have determined how to boot from a USB, and by trying Ubuntu and using Gparted I can see that the partitions are:

sda1: ntfs, Windows RE tools, 499 MB, hidden
sda2: fat32, SYSTEM, 300 MB, boot 
sda3: unknown, blank, 128 MB, msftres
sda4: ntfs, blank, 98 MB, msftdata
sda5: ntfs, SAMSUNG_REC2, 18 GB, hidden diag
sda6: FAT32, SAMSUNG_REC, 1 GB, hbidden diag 

When attempting to do an install from the USB no operating system is recognized (do not know why but it does trouble me). 

Herewith my questions:

I guess that sda2 is the efi boot partition and that during installation I should set this to 'efi boot partition'?
Should I leave sda1, sda3 and sda6 untouched (I don't know what they are for)?
I presume sda5 contains a reinstallable version of Windows? Should I leave it untouched?
sda4 is where I presume I can install Ubuntu (presumably creating two parititions, one for / and one for swap?

With grateful thanks for any help.

Martin

---

### Post by Ubi_one_2014 on 2014-04-20
as far i understand, start the installer, and let ubuntu decide how the partitions will be handled

let ubuntu choose the disk where is will be installed, when you have 1 Hd this is very easy
backup everything before you do this

---

### Post by aridus on 2014-04-20
Many thanks - this was my anticipation but it does not decide (options provided are erase disk, or do something else).

With thanks, Martin

---

### Post by fantab on 2014-04-20
Post the output of the following commands from Live Ubuntu:

```
sudo parted -l
sudo fdisk -l
```

And also post a full window screen shot of your HDD from Windows, if possible.

---

### Post by Ubi_one_2014 on 2014-04-20
> **aridus said:**
> Many thanks - this was my anticipation but it does not decide (options provided are erase disk, or do something else).

With thanks, Martin

i have to recall some memories
but is ubuntu not able to erase all partitions and create new installation environment, like new partitions by itself

---

### Post by aridus on 2014-04-20
Many thanks and please see below (unsure what, exactly you want me to take a screenshot
 of in Windows):

ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA SAMSUNG MZMTD128 (scsi) 
Disk /dev/sda: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 

Number  Start   End    Size    File system  Name                          Flags 
 1      1049kB  524MB  523MB   ntfs         Basic data partition          hidden, diag 
 2      524MB   839MB  315MB   fat32        EFI system partition          boot 
 3      839MB   973MB  134MB                Microsoft reserved partition  msftres 
 4      973MB   107GB  106GB   ntfs         Basic data partition          msftdata 
 5      107GB   127GB  20.2GB  ntfs         Basic data partition          hidden, diag 
 6      127GB   128GB  1074MB  fat32        Basic data partition          hidden, diag 


Model:   (scsi) 
Disk /dev/sdb: 1944MB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

Number  Start   End     Size    Type     File system  Flags 
 1      1855kB  1944MB  1942MB  primary  fat32        boot, lba 


ubuntu@ubuntu:~$ sudo fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 


Disk /dev/sda: 128.0 GB, 128035676160 bytes 
256 heads, 63 sectors/track, 15505 cylinders, total 250069680 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x9cb0db1c 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1  4294967295  2147483647+  ee  GPT 

Disk /dev/sdb: 1944 MB, 1944059904 bytes 
46 heads, 45 sectors/track, 1834 cylinders, total 3796992 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000f237c 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        3624     3796991     1896684    c  W95 FAT32 (LBA)

---

### Post by aridus on 2014-04-20
I have two options: (1) Erase everything and install ubuntu, or (2) do something else (the latter requires me to choose the correct parititions for efi, boot etc.). I could do (1) but I am concerned that one or more of the present six partitions is(are) required for booting into the bios etc.

With thanks, Martin

---

### Post by fantab on 2014-04-20
In windows we have 'Disk Management Utility', if we can see what partition is what, ie which partitions is C: and so on, then we can advice you how to go about partitioning for dual boot...
You have 128gb SSD, if I were you I would use 100gb for Windows C: and remainder GB for Ubuntu '/'. 

Did windows come pre-installed on the HDD? What is your machine, laptop/desktop?

However if you want to remove Win8 in favor of Ubuntu then it does not matter... you delete all the partitions on the HDD and create new ones for Ubuntu. If you have DATA to BACKup, then do it.
An easiest way to format the entire disk earasing all partitions and data on it, it to 'create a new partition table'... you can do this with gparted.
[Gparted Tutorial]("http://www.dedoimedo.com/computers/gparted.html") [the info is bit old but vastly relavent].

You can set up Ubuntu partitions as:
250Mb EFI FAT32 'boot' flag (don't forget to place the 'boot' flag on the partition)
25Gb Ubuntu '/' Ext4
2-4Gb Linux SWAP
All the remaining GB '/home' Ext4.

---

### Post by fantab on 2014-04-20
> **aridus said:**
> I have two options: (1) Erase everything and install ubuntu, or (2) do something else (the latter requires me to choose the correct parititions for efi, boot etc.). I could do (1) but I am concerned that one or more of the present six partitions is(are) required for booting into the bios etc.

With thanks, Martin

Yes you can choose the first option and erase windows and install Ubuntu. This will NOT create a separate /home partition, just '/' and swap. With only '/' partition all your files ie system files and your personal data will be on one partition. This not good for the safety of your DATA. You might loose it if for some reason you have to re-install ubuntu.

I recommend that you have a separate /home partition for you personal data and keep system files separate in '/' partition.

Partitions are NOT involved in booting BIOS, its the other way round.

---

### Post by aridus on 2014-04-20
> **fantab said:**
> In windows we have 'Disk Management Utility', if we can see what partition is what, ie which partitions is C: and so on, then we can advice you how to go about partitioning for dual boot...
You have 128gb SSD, if I were you I would use 100gb for Windows C: and remainder GB for Ubuntu '/'. 

Did windows come pre-installed on the HDD? What is your machine, laptop/desktop?

However if you want to remove Win8 in favor of Ubuntu then it does not matter... you delete all the partitions on the HDD and create new ones for Ubuntu. If you have DATA to BACKup, then do it.
An easiest way to format the entire disk earasing all partitions and data on it, it to 'create a new partition table'... you can do this with gparted.
[Gparted Tutorial]("http://www.dedoimedo.com/computers/gparted.html") [the info is bit old but vastly relavent].

You can set up Ubuntu partitions as:
250Mb EFI FAT32 'boot' flag (don't forget to place the 'boot' flag on the partition)
25Gb Ubuntu '/' Ext4
2-4Gb Linux SWAP
All the remaining GB '/home' Ext4.

Many thanks indeed. I don't want to dual boot and therefore I will set up the partitions as you indicate in the last four lines. My only concern is  whether any of the present 6 partitions are essential for the computer to boot into its bios).

With thanks, Martin

---

### Post by fantab on 2014-04-20
Like I said, parittions only become active after BIOS, in your case UEFI... 

If you feel concerned then make a clone or backup of your existing partitions. There are plenty of Windows specific tools to get the job done. [Here's one]("http://www.macrium.com/reflectfree.aspx").

But you don't need that just erase the HDD and recreate partitions. Go through the gparted tutorial.

If you 'create a new partition table' then make sure it is GPT [GUID partition table] and not msdos.

---

### Post by aridus on 2014-04-20
> **fantab said:**
> Yes you can choose the first option and erase windows and install Ubuntu. This will NOT create a separate /home partition, just '/' and swap. With only '/' partition all your files ie system files and your personal data will be on one partition. This not good for the safety of your DATA. You might loose it if for some reason you have to re-install ubuntu.

I recommend that you have a separate /home partition for you personal data and keep system files separate in '/' partition.

Partitions are NOT involved in booting BIOS, its the other way round.

Many thanks and all understood. At the moment I can get into a screen that allows me to do things (such as turning secure boot on or off) by holding down F2 when the computer boots. This is what I would call the Bios, although I do not understand how machines using efi function (it doesn't seem to be quite the same). If I follow your excellent recommendation to use four partitions I was afraid that I would lose this function on F2 - but looking at it now it seems to be a Samsung thing rather than a Windows thing (if that makes sense). There therefore seems no problem in redoing the partitions with gparted.

Again, with thanks for your knowledgeable help, Martin

---

### Post by aridus on 2014-04-20
> **fantab said:**
> Like I said, parittions only become active after BIOS, in your case UEFI... 

If you feel concerned then make a clone or backup of your existing partitions. There are plenty of Windows specific tools to get the job done. [Here's one]("http://www.macrium.com/reflectfree.aspx").

But you don't need that just erase the HDD and recreate partitions. Go through the gparted tutorial.

If you 'create a new partition table' then make sure it is GPT [GUID partition table] and not msdos.

Apologies - I think my last reply overlapped with this one. I will go ahead and use gparted.

Yours, Martin

---

### Post by aridus on 2014-04-22
> **fantab said:**
> Like I said, parittions only become active after BIOS, in your case UEFI... 

If you feel concerned then make a clone or backup of your existing partitions. There are plenty of Windows specific tools to get the job done. [Here's one]("http://www.macrium.com/reflectfree.aspx").

But you don't need that just erase the HDD and recreate partitions. Go through the gparted tutorial.

If you 'create a new partition table' then make sure it is GPT [GUID partition table] and not msdos.

Many thanks and I have now partitioned the disk as you suggested and successfully installed Ubuntu. It restarts in the usual way following installation and appears to run fine. If I then shut the computer down, and restart, it will not boot (a message about all boot options tried appears). This thread [http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824) covers the subject in part but no matter how I change the bios settings, the laptop does not boot and the 'all boot options tried' message appears. The last lines [http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824) refer to potential problems with ' UEFI doesn't detect the GRUB bootloader'. 

I have reinstalled Ubuntu in the hope that I could repair the boot but am now unsure how to (the boot-repair tool mentioned at the end of the thread does not seem to be available).

If you or anybody else have any further ideas I would be grateful!

With thanks.

---

### Post by aridus on 2014-04-22
I am replying to myself here... On second thoughts it seems more appropriate to close this thread, as the subject is solved. I will open a new post with the new subject.

---

