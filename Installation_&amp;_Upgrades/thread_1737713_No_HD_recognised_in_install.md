---
title: "No HD recognised in install"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by leeds_shrew on 2011-04-23
**PROBLEM**:

When trying to install Kubuntu 10.04 32-bit (or Ubuntu 10.04 64-bit) it does not show me any hard drive to partition in the 'Disk Setup' (I've clicked all the buttons on that screen to see if I can encourage it!) and will not let me past that point in the installation process (because, obviously, no root file system has been defined).

**HISTORY**:

I have done something very bad to my computer... As an aid to selling my computer, I decided to (try to) install Windows 7. I booted into a live Ubuntu CD and used Gparted to reformat my hard drive. After several issues with the Windows boot CD I decided to pull up FastBuild Utility, and did something which included deleting LD and Defining LD again. Didn't make any difference with the Win 7 install. **I am now trying to return my computer to a functional state in the sanctuary of Kubuntu 10.04.**

**THINGS I'VE TRIED**:

Tried installing Win XP which I have installed successfully on another computer. Got an error message: "Setup did not find any hard disk drives installed in your computer" - presumed that was because of something I did with FastBuild Utility (2006). I've tried as many different options in this as I think could make a difference and can find very little help for this online.

Booted into DR-DOS and deleted partitions and created a FAT 32 partition.

Booting into the live Ubuntu 10.04 CD again and used GParted to create an NTFS Primary Partition taking up all the hard drive.

As above and deleting all partitions in GParted.

Checking into BIOS and changing the SATA Operation from 'RAID On' to 'RAID Autodetect / ATA' (Now changed back again to the default 'RAID On.')

Loaded Defaults in BIOS - I've been running Ubuntu 10.04 x64 on it since it came out with these settings.

At all points I have tried to install Ubuntu 10.04 64 bit, Kubuntu 10.04 32 bit (and Win XP) with no success.  In the Kubuntu install, when I get to the Disk Setup part of the installation process it offers me no information whatsoever.

**WHERE TO START**:

My hard drive has all partitions deleted because of my last action in GParted. May need to define a partition. What as?

I'm still convinced that my playing in FastBuild Utility (2006) is probably the root cause of this, and so quite likely to be a good place to go to solve this. I think I've set everything as it was, but can't be 100% on that.

**MY COMPUTER**:

Dell Inspiron 1721, AMD Turion x64 dual core, FUJITSU MHW2120BH 120GB HDD.

[CENTER]**Thank you to anyone who can make suggestions to try ****or ****help**** in any way - sorry I will not be able to reply to any questions straight away as I will not be back on until tomorrow afternoon.**
 [/CENTER]

---

### Post by leeds_shrew on 2011-04-24
Bump

---

### Post by coffeecat on 2011-04-24
> **leeds_shrew said:**
> Checking into BIOS and changing the SATA Operation from 'RAID On' to 'RAID Autodetect / ATA' (Now changed back again to the default 'RAID On.')

Do you have a RAID array, or not? Or if not, was your HD once used in a RAID? If you have a single disc which was once used in RAID, residual RAID metadata can be present which confuses the installer and it shows no discs at all. This is as good an example as any:

[http://ubuntuforums.org/showpost.php?p=10435866&postcount=5](http://ubuntuforums.org/showpost.php?p=10435866&postcount=5)

You'll see that fdisk is showing two partitions but the installer's "allocate drive space" cannot see anything. Is this what you are seeing?

Also - I've not heard of  FastBuild Utility. What is it?

---

### Post by leeds_shrew on 2011-04-25
> **coffeecat said:**
> Do you have a RAID array, or not? Or if not, was your HD once used in a RAID? If you have a single disc which was once used in RAID, residual RAID metadata can be present which confuses the installer and it shows no discs at all. This is as good an example as any:

[http://ubuntuforums.org/showpost.php?p=10435866&postcount=5](http://ubuntuforums.org/showpost.php?p=10435866&postcount=5)

You'll see that fdisk is showing two partitions but the installer's "allocate drive space" cannot see anything. Is this what you are seeing?

Also - I've not heard of  FastBuild Utility. What is it?

Thanks,

It's a single hard disk, and I've never messed around with the hardware since I bought it, but it was a RAID array I think - FastBuild flashes up when I boot up the computer telling me information about the disk:

ID: 1; Mode: 1 +0 RAID 0; Size: 119000M; Track-Mapping: 14467/255/63; Status: Functional.  Then: Press <Ctrl-F> to enter FastBuild (tm) Utility...

If I've changed any of this information by messing around in FastBuild, I don't know what (if any).

**INFORMATION ABOUT FASTBUILD UTILITY:**

When I enter FastBuild Utility, I am given the following options:

View Drive Assignments ... [1]
Define LD ........................ [2]
Delete LD ........................ [3]

I don't even know what LD stands for, but I decided that it must be wise to choose option 3 and get rid of them (it - there was only one).

Then, I defined a new one. The options I can change are as follows:

[Define LD Menu]
LD No --** LD 1** (unchangeable)
RAID Mode -- **RAID 0**, RAID 1 or JBOD
Total Drv -- 0 (changes to **1** once assigned below)
Stripe block -- (if RAID 1 or JBOD = NA) if RAID 0 = 64 KB or **128 KB**
Fast Init -- **ON** or OFF

[Drives Assignments]
Channel : ID -- **1 :Mas** (unchangeable)
Drive Model -- **FUJITSU MHW2120BH** (unchangeable)
Capacity (MB) -- **120035** (unchangeable)
Assignment -- N or **Y** (changes the Total Drv value above)

When I save the settings (bolded above) it says: <Press Ctrl-Y if you are sure to erase MBR!> which I did. It then comes up with "Press Ctrl-Y to Modify Array Capacity or press any other key to use maximum capacity . . .".  I went for max capacity.

**POST CONTINUED:**

[I've now reformatted my HD to 1 NTFS partition using GParted to check again]

The post you provided shows exactly what I see in the installer: nothing!

fdisk -l now reads

Device Boot -- /dev/sda1
Start -- 1
End -- 14593
Blocks -- 117219241
Id -- 7
System -- HPFS/NTFS

(Sorry I can't provide screen shots)

-----------------------

Right. I'm going to read through the thread you've linked to to see if there's any solution in there, because it seems like it might be a similar problem. I'm away for a couple of days so wont be doing any work on it for a while. As always - thanks for any suggestions. EDIT: It wasn't the dmraid solution because I WAS using RAID. I deleted the LD using FastBuild and tried it again and it didn't give me the option to delete the RAID data. LD settings now back to how they were.

---

### Post by coffeecat on 2011-04-25
> **leeds_shrew said:**
> 
Right. I'm going to read through the thread you've linked to to see if there's any solution in there, because it seems like it might be a similar problem. I'm away for a couple of days so wont be doing any work on it for a while. As always - thanks for any suggestions.

The complete thread:

[http://ubuntuforums.org/showthread.php?p=10435866#post10435866](http://ubuntuforums.org/showthread.php?p=10435866#post10435866)

... linked to another thread, which ultimately linked to this:

[http://ubuntuforums.org/showpost.php?p=9447593&postcount=3](http://ubuntuforums.org/showpost.php?p=9447593&postcount=3)

Just to save you the searching. :) Good luck!

---

### Post by leeds_shrew on 2011-05-18
The solution suggested in the 2nd thread didn't work for me, however I have cured this.

First: I used fast build to change the RAID to JBOD. I don't think this should have made any difference as I only have one HD, but I've said it just in case it did.

Second: I booted into the Ubuntu live CD and formatted my HD (again!) Then I **mounted the HD and copied some files into it**.

I could not install Ubuntu with the HD mounted, so it unmounted it automatically as part of the install process (I just used the link on the desktop when you try Ubuntu) but it was then able to see the HD and successfully install :D

---

