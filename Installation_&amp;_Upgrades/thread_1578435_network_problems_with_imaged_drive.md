---
title: "network problems with imaged drive"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by Z.K. on 2010-09-20
I was wondering if I clone a drive, is there a way to not have the network MAC addresses of the original hardware stay with the image.  I need a way to image a system and be able to put the drive on different, but identical hardware except for the MAC addresses of the Ethernet and wireless hardware.

---

### Post by Z.K. on 2011-02-19
> **Z.K. said:**
> I was wondering if I clone a drive, is there a way to not have the network MAC addresses of the original hardware stay with the image.  I need a way to image a system and be able to put the drive on different, but identical hardware except for the MAC addresses of the Ethernet and wireless hardware.

Okay, I guess I will just answer myself since I found something on the Internet while researching how to setup a tftp server.  This link

[https://www.icts.uiowa.edu/confluence/display/ICTSit/USB+Bootable+Clonezilla+PXE+server]("https://www.icts.uiowa.edu/confluence/display/ICTSit/USB+Bootable+Clonezilla+PXE+server")

describes a way to fix this problem so the current board's MAC addresses are the always eth0 and eth1.  See Part 6.

I have not actually tried it yet, but it looks promising.  Hopefully this will help someone else besides me as well.

:D

---

