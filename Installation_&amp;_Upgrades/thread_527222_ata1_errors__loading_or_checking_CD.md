---
title: "ata1: errors  loading or checking CD"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by gilesaj on 2007-08-16
There seems to be a bunch of posts from people with thw ata error and I haven't seen one that we resolved yet.  I have read most of them and tried a few of the recommendations.

I have a new PC that was built the other day. I have done the memory check and it did not find any errors.


[ASUS P5L-MX motherboard]("http://ca.asus.com/search.aspx?searchitem=1&searchkey=P5L-MX")
Core2 Duo E6420 CPU
Kindston DDR2/667 I gig RAM
Western Digital 160G IDE HD

I am not having much luck with this PC loading Ubuntu.

I downloaded the iso for ubuntu 7.04 64 bit desktop and the checksum was OK.  I burned the CD and when booted the menu comes up fine but as soon as I try to install / run or check the CD options I get the same error.

I have tried with both the IDE compatabiluty options SATA PATA and SATA+PATA  and both modes and get the same messages when either are selected.   

The Ubuntu logo comes up and the bar moves back and forth then it drops into Busy Box. 
The error messages that I get repeat over and over again but start with:

/bin/sh can't access TTY  job control off
Initramfs [large number] ata1.01 exception
then the rest repeat over and over again

[large number] ata1: port failed to respond
[large number ata1:01 exception Emask0x0 SAct 0x0 etc etc  frozen
[large number] ata1:01 cmd 000000000 00000000 00000000   tag 0 cdb 0x28 etc etc etc data 512 in

after a while this one is added:

Buffer I/O error on device sdb, logical block 0


The disk is new but has been tested and works.  

I have a failed install of Centos on the disk............

Ant help would be appresiated

---

### Post by phidia on 2007-08-16
Hi, i've recently seen errors similar to that when a ide cdrom/dvd drive doesn't have the correct drivers and specifically with 64 bit linux versions. Since you are using 64 bit feisty you could also search and post in that forum [here]("http://ubuntuforums.org/forumdisplay.php?f=134").
Not sure exactly what to recommend but if i was seeing that i would try the alternate cd and see if that allows you to install.

---

