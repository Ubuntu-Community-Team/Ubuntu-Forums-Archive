---
title: "Bad Scetor/Partition Problems"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by grogger13 on 2007-02-20
I recently decided to install ubuntu on my E1705, 2.0GHz Core Duo, 1GB ram, ATI 1400x radeon.  It has a 120 GB 5400 RPM Western Digital Harddrive.  I looked over a couple tutorials and Alan Pope's video on youtube and decided it would be a fairly easy thing to do, if everything went right.

I defragmented my harddrive, started up Ubuntu Edgy live cd, and went through the steps until i got to the partition editor.  This was were i choose the first option of auto resizing(option 1, as demonstrated by Alan Pope).  This was where the machine just hung and i waited about an hour before I decided it was not working, and rebooted.

Next, I went back to the installer and at the partition editor i chose the last option, manually edit partitions.  I set the NTFS size to half and left half for linux, then set a linux partition, and left 500MB for the grub loader and made a swap partition.

          This was were i got my first error, right at the start i might add.

_______________________________________________________________________

GParted 0.2.5

Resize /dev/sda1 from 110.38 GiB to 55.19 GiB    ( ERROR )
     	
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 118518026752 bytes (118519 MB)
Current device size: 118518027264 bytes (118519 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 37378 MB (31.5%)
Collecting resizing constraints ...
WARNING: The disk has bad sector! This can cause reliability problems!
Bad clusters: 783496 - 783498
ERROR: The NTFS volume has at least 3 bad sectors.
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. *
* The reliability of the disk may stay stable or degrade fast. We suggest *
* making a full backup urgently by running 'ntfsclone --rescue ...' then *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************

========================================

Create Primary Partition #1 (ext3, 54.70 GiB) on /dev/sda

========================================

Create Primary Partition #2 (linux-swap, 500.44 MiB) on /dev/sda

========================================
__________________________________________________________________________


So then i ran Checkdisk actually 3 times and decided to try the install again.  (same error)

Then i went back into windows and ran another defrag from windows.  Searching on the internet i found the program PerfectDisk and partitioned my harddrive again with the PerfectDisk with the "aggresive free space consolidation" option.  i ran that twice.

Again install wouldn't work so i tried to partiton with the System Rescue CD and follow the commands on the Windows Dual Boot tutorial here, but the command wasn't recongnized and i did know how to get it working.

So then i tried Gparted live cd, but in there it wouldn't let me touch the the NTFS partition, except for adding the 7MBs of unpartitioned space.  So i decided to go back into Ubuntu to see if maybe the error message was the same.

Next install try i recieved the same error, so i went back to the internet for more searching and came across Spinrite. I then ran Spinrite on level four to try and fix the bad sectors, but once it got to about 2.7% it seemed to hang(althought it was moving, it had estimated around 13 hours, but the time wasn't changing at all).  i had to stop this because after every piece of data it would beep(i live in a dormroom and its 3o'clock and my roommate would be pretty pissed if i made him go to sleep with that, not to mention me)

First off, I just got this computer in August and if i have bad sectors on the drive already does anybody know if can i get a new one(i have a 3 year warranty).

Secondly, i saw in the error message from Gparted about "ntfsresize", but i do not know what that is.

Is there any way to work aroudn this problem, i really want to get ubuntu up and working.

---

### Post by grogger13 on 2007-02-20
Continue,

I downloaded Partition Magic and it partitioned the drive, but in the Linux partition there is 1.8GB of used spaced already even though i haven't touched it.  So i chose browse with the PartMAgic and all that it showed was one folder labeled "lost+found" but nothing in it.

Are there some misplaced windows files that weren't moved and left in my linux partition?

---

### Post by Fallz on 2007-04-25
I actually have had pretty much the same problem, except I didn't go to the extent of partitioning with a different prgram other than Gparted / ubuntu. 

I ran scan disc and it found no errors in the hdd though, though I ran it twice with chkdsk /r.
I honestly don't know what to do, and am about to give up.

But, should I be worried that ubuntu found a bad sector, but chkdsk didn't? I don't want my hdd to be crashing any time soon.

---

### Post by Mrs Twaddle on 2007-10-23
> **Fallz said:**
> I actually have had pretty much the same problem, except I didn't go to the extent of partitioning with a different prgram other than Gparted / ubuntu. 

I ran scan disc and it found no errors in the hdd though, though I ran it twice with chkdsk /r.
I honestly don't know what to do, and am about to give up.

But, should I be worried that ubuntu found a bad sector, but chkdsk didn't? I don't want my hdd to be crashing any time soon.

i'm getting this too.
Windows says all is well, Linux says No.

I'm more inclined to believe Linux, but i need to  resize my windows partition :confused:

---

### Post by psusi on 2007-10-23
It appears to be complaining that you have 3 sectors that have already been found to be bad and marked as such by chkdsk.  Let's check the disk for any more errors and try to recover those 3 bad sectors.  Boot the livecd and enable the universe repositories and install the smartmontools package.  Assuming your disk is /dev/sda, do this:

sudo smartctl -a /dev/sda

And post the output here.  

It is possible that those 3 sectors can be recovered and there is no further damage to the disk, but I do not know of a way to do that which does not involve destroying your existing windows install.  If there are more problems, then you will want to get it replaced under the warranty.

---

### Post by jazzysmith on 2007-10-24
I have the same problem. What I had planned on doing was: making a copy of the partition as is, replacing the copy with a new one periodically, and storing it on another disk in case I lose the primary one.

Then hopefully I would be able to restore from the copy to a new disk if I have a larger failure.

I haven't been able to get a successful copy, so far.

JS.

---

### Post by krazedkaoz on 2007-10-25
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: ATA      SAMSUNG SV1203N  Version: TQ10
Serial number: S01CJ10W777691      
Device type: disk
Local Time is: Thu Oct 25 19:16:02 2007 UTC
Device does not support SMART

Error Counter logging not supported

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging

---

### Post by matjoeman on 2007-12-02
I'm getting something similar.

Tried to resize my NTFS partition, GParted runs ntfsresize, which complains about bad secotors.  It tells me to run chkdsk \R under windows.

Chkdsk \i tells me that there are bad sectors.  chkdsk \R just runs without doing anything, and afterwards, chkdsk \i still says that there are bad sectors.

This is really annoying because I have 15GB free on the NTFS and have 0KB free in ext3.

---

