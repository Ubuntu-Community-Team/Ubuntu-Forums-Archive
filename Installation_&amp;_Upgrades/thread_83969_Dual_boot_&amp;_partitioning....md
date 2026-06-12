---
title: "Dual boot &amp; partitioning... ?"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by LinuxLumox on 2005-10-30
I'm relatively new to computers. Most of what I've learned over these last several months was through stumbling to build one from scratch. I've never been great reading manuals; old age and eye disease have made wading through documentation quite tedious. By trials & error (and I mean trials indeed, especially setting up the system bios, which seems now to work, but only just, and may still be improper), I was eventually able to install and boot up Windows XP/SP2 --  a spiritual moment.

Thereafter I installed broadband Internet and began poking around this incredible cyber world. Jumping hither and thither, forums and tech sites, I became convinced my hard drive configuration and XP installation are less than ideal. Since I'm going to reformat and reinstall everything, I thought I might try a Linux distro for comparison, and, perhaps, better security. I just downloaded ubuntu-5.10-install-i386.iso, [57 min., 1 sec]. I believe I must now 'burn' this file to a CD, which I've never done, but feel reasonably confident I'll muddle through.

Here's my immediate request for recommendations: I have four hard drives [the used IDE's are gifts]: 1 300GB Seagate, 1 200GB WD, both SATA's, 1 40GB, 1 20GB, both WD IDE's. I've been struggling with partitioning concepts, I don't understand the distinction from logical drives, and feel very unsure of my impressions. My very tentative idea is install the OS's, Windows and Linux, on the first partition of each of the SATA drives and to use the IDE drives for temp files only, including DVD burn staging/video editing.

Does this make any sense and/or what would be an ideal setup, what partitioning configuration would you suggest? I'm confused about setting up a 'dual-boot'. I guess I'm assuming I'll be able to chose which drive to access when I power up.

As you can see, I've bitten off quite a lot; I've the enthusiasm of a new convert. I've no choice but to chew. And spit-ups seem rather inevitable. Any one who wipes my chin is due great thanks.

---

### Post by GaryG on 2005-10-30
Since you are just starting out I suggest getting removable trays and keep the OS on separate drives.

---

### Post by zaguar on 2005-10-30
Consider Trying this: 

HDA 40GB IDE
10GB Windows Root Partition (NTFS)
5GB-10GB Program Files (NTFS)
The Rest Documents and Settings (FAT32)

HDB 20GB IDE
Entire Drive FAT32

SDA 300GB SATA
300GB ReiserFS or ext3


SDB 200GB SATA
50MB ( /boot ) ReiserFS
10GB Ubuntu ( / ) Partition (ReiserFS)
10GB Other Distribution
10GB Other Distribution 
1-1.5 GB swap
10GB ( /home ) partition ext3 or ReiserFS
The Rest can be FAT32, EXT3 or ReiserFS

Reasoning: HDA:
NTFS has higher performance, and having the windows root on a seperate partition allows for easier maintainence in the long run.  Having Documents and Setting as FAT32 allows for easy read/write access from both Ubuntu and Windows.  

HDB:
This can be used as a staging drive easily for DVD burning etc.  FAT32 for compatibility.

SDA:
This is the difficult one.  I don't know what you want from this one.  I made it out to be a multimedia drive, so entirely ReiserFS.  Another alternative is ext3.  Although it has less performance than reiserFS, it can be intergrated into windows through [this driver]("http://www.fs-driver.org/").  Your Call.  

SDB:
This is the linux partition. It has /boot and /home seperate, for easier upgrading.  /home can be ext3,2 or Fat32.  This allows you to read from windows.  

The root partition for ubuntu is reiserFS for performance. 

The other partitions are for the daty that, if you are anything like me, you will install other distro's on it  I have had Gentoo, Mepis, Ubuntu and Kubuntu all on my Desktop at one time or another.

The rest is your choice. I don't know what for, though, maybe another multimedia partition?  

This is my suggestion, you can look at it and consider it, and tell us what you need.  Do you have a huge DVD backup system, do you need read/write access from Linux and Windows to /home and My documents?  

PS: If you need to burn an iso, download [this]("http://isorecorder.alexfeinman.com/isorecorder.htm"), install it, right click on the .iso and there should be an option to **copy to disk**.  

PPS:  If you are nervous, don't be.  Backup your data to an external source (like a CD/DVD) and go for it!

PPPS:  If you need help on partitioning basics, read the Gentoo install guide.  It is a great resource and it helped me understand what was going on.

---

