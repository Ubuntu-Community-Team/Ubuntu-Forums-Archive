---
title: "to upgrate I need to increase my linux partion."
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by clausrei on 2011-09-20
Hi,
 
would like to upgrate from Karmic Koala. For that reason I need increase my ext4 partition for more than a 1 GB. Now GParted shows a key (which very likely means it is locked) on my NTFS partition and ext4 partition.

What do I have to do in order to get it unlocked, to increase my ext4 partition decrease my NTFS partition.

Thank you for your help !

Claus

---

### Post by clausrei on 2011-09-20
[QUOTE=clausrei;11268995]Hi,
 
would like to upgrate from Karmic Koala. For that reason I need increase my ext4 partition for more than a 1 GB. Now GParted shows a key (which very likely means it is locked) on my NTFS partition and ext4 partition.

What do I have to do in order to get it unlocked, to increase my ext4 partition decrease my NTFS partition.

Thank you for your help !

Claus

---

### Post by Hakunka-Matata on 2011-09-20
Hi, Wilkommen;

Yes, the key means it's locked.  The partition is in use, because you've booted that partition.  Boot from a LiveCD/USB and use gparted then.  Your swap partition will likely be mounted, even when booting from CD, and if it is in an Extended partition, that may also be mounted.  So turn off swap "right button, swapoff", and unmount the extended partition, if necessary.

Clean installs sometimes work better than upgrading.

---

### Post by Mark Phelps on 2011-09-20
Word of caution ...

If you're running Vista or Win7, do NOT use GParted to shrink the OS partition.  These two Windows OSs are very touchy about filesystem changes from "other" products.  Making such changes using GParted runs the risk of corrupting the filesystem and rendering Windows unbootable.

If you're running XP, then you should be OK.

---

### Post by clausrei on 2011-09-21
Thank you for the warning. I am running XP so I sould be fine, and I done a backup.
 
But I still don't know how to do it.

---

### Post by Mark Phelps on 2011-09-21
> **clausrei said:**
> But I still don't know how to do it.

OK, then you will need to boot using the Ubuntu CD because you can't change partitions while they are mounted, and if you run from Ubuntu on your hard drive, it will mount the partitions.

Select the Try Ubuntu option.  When you get to a desktop, open Gnome Partition Editor (Gparted).  You will see a windows displaying the partitions on your drive.

Select the WinXP partition and shrink the size.  Be patient, as GParted is known to be slow and can take quite a while.  Don't interrupt it or shut down your PC while it's running.

Then, if your Ubuntu partitions are inside an Extended partition, select that and expand it to fill the now unallocated space.

Then, select your Ubuntu partition and expand it to fill the space inside the Extended partition.

When done, reboot.

---

### Post by clausrei on 2011-09-23
Thank You ! :D

---

### Post by clausrei on 2011-09-30
Ok, did boot from CD now and could start the re-sizing of the partitions.  But I am not quite there yet, I had an error message on the screen, If some one could help me to make sense out of it ? The error report I is as  followed: [SIZE=2]

[/SIZE]GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Shrink /dev/sda1 from 32.90 GiB to 30.07 GiB  00:00:36    ( ERROR )
         
calibrate /dev/sda1  00:00:00    ( SUCCESS )
         
path: /dev/sda1
start: 63
end: 68999174
size: 68999112 (32.90 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:11    ( SUCCESS )
         
ntfsresize -P -i -f -v /dev/sda1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 35327541760 bytes (35328 MB)
Current device size: 35327545344 bytes (35328 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 26380 MB (74.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 35042 MB 0
Multi-Record : 35308 MB 32095
$MFTMirr : 20000 MB 1
Compressed : 35308 MB 122424
Ordinary : 35327 MB 119311
You might resize at 26379247616 bytes or 26380 MB (freeing 8948 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:14    ( ERROR )
         
run simulation  00:00:14    ( ERROR )
         
ntfsresize -P --force /dev/sda1 -s 32284191743 --no-action
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 35327541760 bytes (35328 MB)
Current device size: 35327545344 bytes (35328 MB)
New volume size : 32284185088 bytes (32285 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 26380 MB (74.7%)
Collecting resizing constraints ...
Needed relocations : 521072 (2135 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:11    ( SUCCESS )
         
ntfsresize -P -i -f -v /dev/sda1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 35327541760 bytes (35328 MB)
Current device size: 35327545344 bytes (35328 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 26380 MB (74.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 35042 MB 0
Multi-Record : 35308 MB 32095
$MFTMirr : 20000 MB 1
Compressed : 35308 MB 122424
Ordinary : 35327 MB 119311
You might resize at 26379247616 bytes or 26380 MB (freeing 8948 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:00    ( SUCCESS )
         
run simulation  00:00:00    ( SUCCESS )
         
ntfsresize -P --force /dev/sda1 --no-action
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 35327541760 bytes (35328 MB)
Current device size: 35327545344 bytes (35328 MB)
New volume size : 35327541760 bytes (35328 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
         
ntfsresize -P --force /dev/sda1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 35327541760 bytes (35328 MB)
Current device size: 35327545344 bytes (35328 MB)
New volume size : 35327541760 bytes (35328 MB)
Nothing to do: NTFS volume size is already OK.

**I just checked this last message, the NTFS partition has not changed its size. **!!?? And I tried to increase it on more than 2.9 GB. 


Claus

---

### Post by clausrei on 2011-10-23
Hi,


I finally couldn't  re-size the partition from my old Karmik Koala  Ubuntu CD for what ever reason. But I have downloaded the GParted live  CD and with this tool I managed to  shrink the NTFS partition. 

Now, I have a new problem: I can move the smaller NTFS, which is  visually located left, into the empty space, I can grow the NTFS again  and I can format the empty space with any File System I like ( have  formatted it to ext4 for now) 

Ubuntu recognize the new partition but I can't merge the two ext4  partitions on this hard disc drive. I guess it will be important, when I  am upgrading ?!

Any idea ?!

Claus 

PS: Another option would be to just install the newest Ubuntu on top.  But I am not so happy, because I loose all the software I am using,  which would have to be re-installed. But maybe this will be the only  option, if I can't find a solution to merge the two ext4 partitions.

Who ever has the same problem and read this post, I recommend to read  the Info file on the GParted Live CD after booting from the burned CD.   There have been some cases where people could not log-on to their  Windows XP anymore, because Windows could not find the new right size of  the NTFS partition and you have to delete a Registry Key 
(HKEY_Local_Machine\system\MountedDevices. ) However I didn't have any problems and everything worked fine.

---

### Post by Hakunka-Matata on 2011-10-23
Please let us see how your disk is partitioned, post the output of ```
sudo fdisk -l
``` wrapped in [code]tags.

---

### Post by clausrei on 2011-10-23
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3d0e3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3892    31257568+   7  HPFS/NTFS
/dev/sda2            4296        4864     4570492+   5  Extended
/dev/sda3            3892        4295     3241984   83  Linux
/dev/sda5            4296        4832     4313421   83  Linux
/dev/sda6            4833        4864      257008+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by clausrei on 2011-10-23
[[IMG]http://img402.imageshack.us/img402/5994/gpartedparion.png[/IMG]]("http://imageshack.us/photo/my-images/402/gpartedparion.png/")

Screen shot taken, while partitions have been mounted.

---

### Post by Hakunka-Matata on 2011-10-23
```
=clausrei;11384192Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3d0e3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3892    31257568+   7  HPFS/NTFS
/dev/sda2            4296        4864     4570492+   5  Extended
/dev/sda3            3892        4295     3241984   83  Linux
/dev/sda5            4296        4832     4313421   83  Linux
/dev/sda6            4833        4864      257008+  82  Linux swap / Solaris

Partition table entries are not in disk order
``` I'm posting the fdisk -l output back to you so you see how it looks when posted in [code]tags instead of [quote]tags. 
 It really is easier to take in when formatted like this. 
Now to the task:

The ntfs partition has a problem, needs to have chkdsk run against it or run a 'check' against it using gparted.  Right button on partition, select 'check'.  

Gotta shrink the ntfs partition, what went wrong there for you?

Have a quick look in the Ubuntu partitioning link in my signature for example partition sizing.

---

### Post by clausrei on 2011-10-24
Hi I have run Check but no error has been found. Report was just: Check complete !?

Now, I have deleted the new ext4 again and tried to expand the Extendend partition, but it produced an error message in Gparted Live CD after starting it. 

The screenshot below is from while booting from Ubuntu Live CD. I don't understand why the extended is locked I have unmounted all drives ?? 


[[IMG]http://img33.imageshack.us/img33/4707/screenshotdevsdagparteds.png[/IMG]]("http://imageshack.us/photo/my-images/33/screenshotdevsdagparteds.png/")

---

### Post by Hakunka-Matata on 2011-10-24
Ok, you're moving in the right direction, 
Extended is locked, because the swap partition is in use. The  swap partition resides inside the Extended partition.  Even though you're running off liveCD and RAM, the OS finds swap partitions and will use a swap(s) partition if it finds one.  Right click on swap, and click '**swapoff', **then you can unmount Extended.  It's ok to turn off swap.
the nfts partition's warning triangle should be fixable by booting the ntfs partition (windows xp?) and running chkdsk /r or chkdsk /f, repeatedly until it reports no errors.  If it finds an error and fixes it, run chkdsk again, and again, until it reports no errors.

---

### Post by clausrei on 2011-10-25
Fantastic !

It worked perfectly fine !

I also have done a "chkdsk /r" check in Windows XP, but no Error has been found. However, the yellow triangle  at the NTFS partition appears only when I start Ubuntu and Gparted from hard disk drive. It does not appear when booting from CD Room. 


Thank you very much for your help !  
:D

---

### Post by Hakunka-Matata on 2011-10-25
You are welcome, glad to see you've resolved the issue.

---

