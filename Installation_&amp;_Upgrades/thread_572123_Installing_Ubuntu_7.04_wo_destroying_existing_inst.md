---
title: "Installing Ubuntu 7.04 w/o destroying existing installation"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by tomcat2007 on 2007-10-10
Hello, Linux newbie here.  After playing around with several versions of the Ubuntu 7.04 Live CDs, I have decided to make the jump to Linux, but I'm not quite ready to totally give up Windows (although that is the eventual goal)

I would like to install the 32 bit i386 Feisty Fawn on my HP Pavillion dv9000z which has an AMD Turion T-60 2GHz dual core 64 bit CPU, 2GB RAM, 160GB HD (with a 128GB & 21GB partitions), a Broadcom 4311 wireless chipset, NVIDIA graphics (1440x900x32), and an existing Windows XP SP2 installation which I want to retain intact.  I tried the 64 bit version but prefer to wait until 64 bit computing becomes more mainstream.

Primary use of the laptop is watching movies (XVID), listening to music (MP3), Internet surfing, writing documents, remote access using SSH & RDC, and some gaming.  All critical data has been backed up and installation is ready to proceed.

Being a newbie to Linux, I have two major concerns at present:

Finding a step by step process for installing Ubuntu without destroying Windows & configuring Ubuntu to use both CPU cores.  It is my understanding that the partition editor has to be used for the prior concern and the Kernel must be recompiled to satisfy the second... which has a side effect of requiring a reinstallation of NVIDIA drivers.

Anyhoo, I looked through documentation at help dot ubunta dot com and here on this forum regarding the first concern but wondered if someone here has some links to more detailed instructions.  Anyone care to help the journey toward a home with a bunch of nifty Microsoft coasters? :lolflag:

---

### Post by tomcat2007 on 2007-10-10
Okay, after some more scavenging for information I was able to successfully install Ubuntu... in fact, it was much easier than I had initially expected, encountered no problems whatsoever.  Haven't booted to XP since the install but the option is right there at the bottom of the list under "Other Operating Systems."

I then configured my ethernet (still haven't got the wireless working), turned off the infuriatingly sensitive tapping, installed the NVIDIA drivers, flash, the DIVX, XVID, & MP3 codecs, and got a couple accounts configured in GAIM.  

I was wondering if there is a way to see if both CPU cores are being utilized?  My research (such that it is) indicated that only CPU0 would be used unless the Kernel was modded.

Tomorrow morning I'll be working on the wireless (Broadcom 4311) but I understand that one is pretty tricky.  Any tips or URLs would be appreciated.

---

