---
title: "Cannot get usb install to work"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by reluttr on 2011-02-03
Basically I followed the "how to make a USB install drive" guide on ubuntu's main site. 

But when I go to actually boot the drive in my netbook I only get this text on the screen.

> SYSLINUX 4.02 2010-07-21 EDD Copyright (C) 1994-2010 H. Peter Anvin et al

I dont understand what I am doing wrong... I open the Universal USB Installer, choose ubuntu 10.10 on the list, find the ISO on my computer, and select my drive, check the box to format the drive and start the process.

It almost has to be a bug in the USB program, its like its not configuring the boot MBR correctly.

---

### Post by C.S.Cameron on 2011-02-03
I don't understand why they mention Universal when a better Startup Disk Creator is on the Live CD.
If you can't boot the Live CD you can extract usb-creator from the iso and run it in windows.

Firs check the MD5SUM of the iso: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by towheedm on 2011-02-03
This happened to me also.  I downloaded the iso, ran the usb startup disk creator as stated in the ubuntu wiki and got a stuck screen at the boot prompt that appears after the SysLinux message.

What worked for me is this:
When the boot prompt appears, type help and press enter.  The install process successfully after that.

---

