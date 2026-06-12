---
title: "Ubuntu Studio 11.04 64-bit Format/Partition Questions"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Bobsteroid on 2011-05-19
Ubuntu Studio 11.04 64-bit Format/Partition Questions
 
I would like to install Studio on an external 2TB drive hooked to my computer via eSATA cable. Booting from the DVD, I got as far as the partition/format screen, got confused, then aborted the install.
 
The computer usually boots to Win7 running on an AMD 64x3 machine. I'd like to be able to use about 1.5 TB of the external drive to back up another external drive I have AND to possibly backup an image of my internal hard drive. That part of the drive will be NTFS.
 
The other 500GB of the external drive I'd like to devote to Studio and I'm pretty sure I can boot to the eSATA drive if I select it in the BIOS.
 
_Question 1_: once Studio is installed, can I create a "boot" CD that will bring me to Ubuntu without having to play with the BIOS? In other words, just pop the CD in while BIOS starts if I want to use Ub. Otherwise the computer will boot to Win7.
 
_Question 2_: in creating the 500GB "free space, Ub. asks if I want to put it at the beginning or the end of the drive. I want the beginning, correct?
 
_Question 3_: how should I proportion the 500GB between the various Ub. partitions (swap, "/", home, ...) and what partitions should I create? I figure swap will be 10GB since I have 4GB memory. In which order should they be created?
 
_Question 4_: What file system should I use with each partition?
 
_Question 5_: Should I create a "share" partition in FAT32 to share files between operating systems? Or can I write to NTFS?
 
I've done a bit of research but still haven't found information covering my specific scenario (ie: external eSATA drive shared with windows). 
 
Thanks for your help, Bob :D
 
PS: the external drive is currently unformatted. 500GB is the max I'd like to devote to Ub. although less would be good, too. ;) I'm thinking there will be plenty of space for audio and video files. And it may not be "on" all the time in Windoze (the drive can be turned off).

---

### Post by zvacet on 2011-05-20
Q2: yes
Q3:install in this order /root home /home swap I think 10GB is too much for swap give 10-15GB to /root and rest for home
Q4:format partitions as ext4
Q5:You can read and write to NTFS

---

