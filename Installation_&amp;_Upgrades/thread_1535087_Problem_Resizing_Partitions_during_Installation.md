---
title: "Problem Resizing Partitions during Installation"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by ztschutt on 2010-07-20
I am trying to install Ubuntu as a dual-boot with Windows XP, but whenever I get to the partitioning part of the installation it stays at 0% for a few minutes and then I get this error:
[IMG]http://farm5.static.flickr.com/4141/4812792736_5e09688ac0.jpg[/IMG]

How do I fix this? Is it because I have free space?

---

### Post by Rubi1200 on 2010-07-20
First, stop what you are doing and explain which option you choose to use.

Some questions: 

Did you create a partition for Ubuntu and how much space did you give it?

Did you make a backup of Windows XP first?

Did you try and create a partition for Ubuntu from _within_ Windows using the built-in Disk Management tool or are you working directly from the Ubuntu CD?

Do you have more than 1 hard-drive installed?

---

### Post by ztschutt on 2010-07-20
I choose the install side-by-side option.

**Did you create a partition for Ubuntu and how much space did you give it?**
I believe that is what this wizard is trying to do. But I have tried to manually resize my Windows XP partition and I get the same error. When I tried to manually create the partition I gave it 7 gbs.


**Did you make a backup of Windows XP first?**
Yes.

**Did you try and create a partition for Ubuntu from within Windows using the built-in Disk Management tool or are you working directly from the Ubuntu CD?**
I'm working directly from the CD. I believe its impossible to resize the Windows XP partition using the Disk Manager.


**Do you have more than 1 hard-drive installed?**
No.

---

### Post by Rubi1200 on 2010-07-20
> **ztschutt said:**
> **Did you create a partition for Ubuntu and how much space did you give it?**
I believe that is what this wizard is trying to do. But I have tried to manually resize my Windows XP partition and I get the same error. When I tried to manually create the partition I gave it 7 gbs.


**Did you make a backup of Windows XP first?**
Yes.

**Did you try and create a partition for Ubuntu from within Windows using the built-in Disk Management tool or are you working directly from the Ubuntu CD?**
I'm working directly from the CD. I believe its impossible to resize the Windows XP partition using the Disk Manager.


**Do you have more than 1 hard-drive installed?**
No.

Ok, first things first.

> I believe that is what this wizard is trying to do. But I have tried to manually resize my Windows XP partition and I get the same error. When I tried to manually create the partition I gave it 7 gbs.7 GB is not enough unless you are planning on a custom install (which I do not recommend). If you have the disk space, you need to give Ubuntu somewhere between 15-20 GB to be on the safe side.

>  Yes.Excellent!!

> I'm working directly from the CD. I believe its impossible to resize the Windows XP partition using the Disk Manager.I think you may be right (I haven't used Windows for so long now!) I do believe it is possible in Vista and 7 though.

I suggest you use GParted which is on the LiveCD to first resize Windows. It can take quite some time. Basically you are shrinking the Windows partition to make space for Ubuntu.

Then, exit and restart. Continue using the LiveCD and run the option to check the disc for defects.

If everything is okay then go ahead and install Ubuntu choosing to install to the largest continuous free space.

Do not choose the side-by-side option because otherwise the installer will put Ubuntu on the Windows partition and you will still be left with the free space you just created.

If anything is unclear or you need more advice, please ask.

VERY IMPORTANT: after resizing make sure you can still boot into Windows before taking the other steps. And if you see a message like this > Windows needs to check your disk(s) for consistencyit is okay. Let Windows do its thing and then continue with the process as above.

---

### Post by ztschutt on 2010-07-20
When I tried to use gparted I got an error. What is the problem? Its suggestion of freeing less space does not work, as I get the same error even with only one mb freed. I have 25 gb free on the C partition.

```
GParted 0.5.1

Libparted 2.2
Move /dev/sda2 to the right and shrink it from 72.95 GiB to 61.51 GiB  00:00:42    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 7823655
end: 160810649
size: 152986995 (72.95 GiB)
calculate new size and position of /dev/sda2  00:00:00    ( SUCCESS )
     	
requested start: 31840830
requested end: 160826714
requested size: 128985885 (61.51 GiB)
new start: 31840830
new end: 160826714
new size: 128985885 (61.51 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:13    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 78329340416 bytes (78330 MB)
Current device size: 78329341440 bytes (78330 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 50964 MB (65.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 60420 MB 0
Multi-Record : 78313 MB 214846
$MFTMirr : 39165 MB 1
Compressed : 78302 MB 229568
Ordinary : 78324 MB 219554
You might resize at 50963116032 bytes or 50964 MB (freeing 27366 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:16    ( ERROR )
     	
run simulation  00:00:16    ( ERROR )
     	
ntfsresize -P --force /dev/sda2 -s 66040773119 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 78329340416 bytes (78330 MB)
Current device size: 78329341440 bytes (78330 MB)
New volume size : 66040766976 bytes (66041 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 50964 MB (65.1%)
Collecting resizing constraints ...
Needed relocations : 757227 (3102 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:13    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 78329340416 bytes (78330 MB)
Current device size: 78329341440 bytes (78330 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 50964 MB (65.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 60420 MB 0
Multi-Record : 78313 MB 214846
$MFTMirr : 39165 MB 1
Compressed : 78302 MB 229568
Ordinary : 78324 MB 219554
You might resize at 50963116032 bytes or 50964 MB (freeing 27366 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda2 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 78329340416 bytes (78330 MB)
Current device size: 78329341440 bytes (78330 MB)
New volume size : 78329336320 bytes (78330 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 78329340416 bytes (78330 MB)
Current device size: 78329341440 bytes (78330 MB)
New volume size : 78329336320 bytes (78330 MB)
Nothing to do: NTFS volume size is already OK.

========================================

```

---

### Post by efflandt on 2010-07-20
WinXP may have some files that cannot be moved (like virtual memory).  So it may be a good idea to first tell XP to check your drive, reboot to do that, then defrag.  Then somewhere in System > Advanced tab is Virtual Memory setting.  You want to write down current settings, then disable virtual memory for now.  You have to reboot for that to take effect.

Once you defrag and disable virtual memory in WinXP you should have a much better chance of shrinking Windows.

After you install Linux, you can re-enable virtual memory in Windows with whatever is previous settings were.

---

### Post by ztschutt on 2010-07-20
Thanks. The defragment is going to take a while. I'll post once I try your suggestions.

**Edit: **The defragment worked, its partitioning the drive right now. Yay!

---

### Post by ztschutt on 2010-07-20
Thanks for all your help! Ubuntu is now happily installed in a 20gb partition in my hard drive, with Windows XP still intact. :D

---

