---
title: "installation of ubuntu 10.10 without erasing the data in other NTFS drives"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by neodumindu on 2010-10-21
I'm using windows 7 now and I want to install ubuntu as the main OS to the current C:drive(which has installed windows currently) but **with keeping the data in other ntfs drivers**(D:, E:, F: ) on my hard disk. I can't take backups of all data in other drivers and if that data erased with ubuntu installation I will face a very big problem in future. So how to install ubuntu 10.10 only for a one drive(c: drive) without erasing the data on other ntfs drivers? thank you

and I uses nvidia 8 series graphic card and are there any special things to follow to install it's official linux drivers(.run) or is it enough to use default drivers on ubuntu.

thank you

---

### Post by neodumindu on 2010-10-23
can anybody help me, I have installed it on VMWare but I fear to install it to the C: drive still because even in the forum someone asked a help to recover deleted data on installation .

The steps he have done.

[LIST=1]
[*]select advance mode on installation.
[*]select the drive and set mount type to /
[*]click formt
[/LIST]
He says the data he had has erased. so can anybody tell me how to install ubuntu 10.10 with out erasing the data in other drivers. :(

---

### Post by efflandt on 2010-10-23
If your computer did not come with discs for Win7, etc. make sure that you create whatever utility or system discs from the manufacturer's utility in Windows, so you can restore that if or when you want to in the future.

Boot an install CD (or USB) to a live system and post the output of: **sudo fdisk -lu**

Or even better would be to run the bootinfo script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) If you post RESULTS.txt here, highlight it and click the **#** in the message window to put code tags around it.

Then you will have a record of how everything was originally and we can tell if you have regular partitions (easy) or something more difficult like logical dynamic volumes.

Different manufacturers might set up things differently.  My Dell uses regular partitions, but already has 3 of them, sda1 is small FAT32 utility, sda2 is the actual boot and RECOVERY partition, and sda3 is Win7 C: drive that it runs from.  So if you are trying to format and install on your C: drive, you have to make sure you have the correct /dev/sda# for that.

---

