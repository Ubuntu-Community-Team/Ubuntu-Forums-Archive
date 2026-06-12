---
title: "Strange Issue..."
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Desert Sailor on 2011-10-17
My story...  Was running 11.04 with no problems. 

Tried Update Mgr to 11.04, Update failed, left system unusable. 

Downloaded 11.10 burned CD and tried for new install.  
This CD hangs with the last 4 lines on the screen....

[ 5.185275] SD 6:0:0:1: [SDD] Attached SCSI Removable Disk
[ 5.188264] SD 6:0:0:0: [SDC] Attached SCSI Removable Disk
[ 5.189020] SD 6:0:0:3: [SDF] Attached SCSI Removable Disk
[ 5.189764] SD 6:0:0:2: [SDE] Attached SCSI Removable Disk
(System hangs here, will accept keyboard input but stops dead) 

I downloaded 11.10 several different times burned new CD's, they all perform the same.  I downloaded 11.04 from the Ubuntu Archives and it hangs at the same place.  

I can install 10.10 from my old ISO CD and it installs fine, but when I try to enable the Nvidia driver the system crashes and will not boot back to X.  I can't restart X without a bunch of Nvidia driver errors. 

Something is wrong with my system because all of the ISO's hang at the same place during install.  Doesn't matter if it is an upgrade or clean install.  

Any help or ideas???  I can wait on installing 11.10, but I would love to get back to 11.04 and not continue with 10.10 at 800x600 resolution. 

AMD Phenom II 965 Q-4
MSI M-board 
2-SATA drives 
EVGA Nvidia Gforce 550 TI

---

### Post by youngunix on 2011-10-17
> **Desert Sailor said:**
> My story...  Was running 11.04 with no problems. 

Tried Update Mgr to 11.04, Update failed, left system unusable. 

Downloaded 11.10 burned CD and tried for new install.  
This CD hangs with the last 4 lines on the screen....

[ 5.185275] SD 6:0:0:1: [SDD] Attached SCSI Removable Disk
[ 5.188264] SD 6:0:0:0: [SDC] Attached SCSI Removable Disk
[ 5.189020] SD 6:0:0:3: [SDF] Attached SCSI Removable Disk
[ 5.189764] SD 6:0:0:2: [SDE] Attached SCSI Removable Disk
(System hangs here, will accept keyboard input but stops dead) 

I downloaded 11.10 several different times burned new CD's, they all perform the same.  I downloaded 11.04 from the Ubuntu Archives and it hangs at the same place.  

I can install 10.10 from my old ISO CD and it installs fine, but when I try to enable the Nvidia driver the system crashes and will not boot back to X.  I can't restart X without a bunch of Nvidia driver errors. 

Something is wrong with my system because all of the ISO's hang at the same place during install.  Doesn't matter if it is an upgrade or clean install.  

Any help or ideas???  I can wait on installing 11.10, but I would love to get back to 11.04 and not continue with 10.10 at 800x600 resolution. 




I can only think of two suspect:

1. you probably burned the CDs using the wrong settings and/or software.
**Solution**: skip burning Ubuntu onto a disk and try this, if you have a usb flash drive with 4GB of storage or more, then make a bootable usb drive using this software [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to clarify any issues related to a corrupt disk.

2. you probably trying to install a 32bit OS on a system with more than 4GB of RAM, just to make sure that isn't the issue, check the system hardware specs.

---

