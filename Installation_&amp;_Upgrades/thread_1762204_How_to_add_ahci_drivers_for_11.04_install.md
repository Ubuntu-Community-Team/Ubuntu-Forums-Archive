---
title: "How to add ahci drivers for 11.04 install?"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by cabatex on 2011-05-18
I recently decided to install Ubuntu 11.04 on a 320gb hitachi sata hard drive.  This is going into a new system with an Asus MB, AMD Proc, not sure if this matters.  Anyway I can not set the bios to use ahci and see the sata drive.  I can only use IDE mode with sata enabled.  Asus support says to install ahci for os.  If I boot into the USB install key and attempt to the install OS I receive a read/write error.  I have another drive on IDE that has 11.04 on it and if I try to format the new drive and partition it with Disk Utility it fails with "Error formatting drive: error creating partition table: helper exited with exit code 1: error calling fsync(2) on /dev/sdb: Input/output error".  I have tried to use dd and fdisk but I don't believe I need these until I do something else first just not sure how or where to look.

---

### Post by cabatex on 2011-05-23
If I do this... 

BUMP

will someone be prompted to reply to this thread?

---

### Post by mockingbird on 2011-05-23
The kernel should come precompiled with the Intel AHCI driver...

---

### Post by cabatex on 2011-05-23
So there is a driver for SATA AHCI contoller in 11.04 that shows the drive information in Disk Utility but I can't format the drive in Disk Utility it gives an error.  Any ideas on where to go with this?

---

### Post by Hedgehog1 on 2011-05-23
Could you tell us the error message you are getting when you try to format?

Also, can you tell us the 'SMART Status' health of the drive?


***The Hedge***

:KS

---

### Post by cabatex on 2011-05-24
The errors were in my first post and SMART shows the disk is healthy.  I can put the disk in another system and it works normally.  

Does anyone have any knowledge of AMD SATA SB7xx Controllers?  I have a sneaking suspicion that my problem lies within the controller but I don't know if it is kernel level driver and if its possible to fix it.

---

### Post by cabatex on 2011-05-25
So perhaps this thread now belongs in the hardware posts because I discovered that other drives work for my system but this Hitachi drive won't work.  I was under the assumption that a 2.5 inch drive would work in a desktop.  I read quite a few forums that talked about power being an issue for the 2.5 inch drive but most people said they had successfully done it with out any changes to their systems, SATA is SATA.  Does anyone have any experience with this?

---

