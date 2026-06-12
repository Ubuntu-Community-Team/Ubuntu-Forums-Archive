---
title: "Are updates stored on flash drive or PC hard drive?"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by FalsEyeVision on 2011-02-01
Hello Everyone!  

I'm new to the forum and Linux, in general.  I've tried various LiveCDs in the past, but I am currently running Ubuntu 10.04.1 off a 2GB Kingston flash drive. 

The flash drive has a new clean install of Ubuntu on it (no personal files yet), but its an older version.  If i run the Update Manager and install updates to get to the latest version (10.10), where will the update files be stored when downloaded? On the flash drive or on the PC hard drive?  

The PC I'm running the flash drive on is not mine, it belongs to another family member, so I would rather not have any files (update or personal) show up on the computer's main hard drive.


Thanks in advance for the help.

---

### Post by Jlayman on 2011-02-01
I believe they would be stored on the flash drive.  Also i dont think the updates will be saved when you shutdown.  I am not positive though.   if you want a updated version i know there is a way to make a customized live usb with the packages you want and probably updates as well.

---

### Post by prshah on 2011-02-01
> **FalsEyeVision said:**
> 
The flash drive has a new clean install of Ubuntu on it <..> but its an older version.  If i run the Update Manager and install updates to get to the latest version (10.10), where will the update files be stored when downloaded? On the flash drive or on the PC hard drive?  

Short answer: a) Update files will be stored on the pendrive.
b) You will not be able to upgrade the OS stored on the pendrive. 

Long answer: If you have setup the USB install to be "persistent", you will have typically setup multiple partitions. At a minimum, that would be 700MB for the live, and at max (for 2GB pendrive) 1.3GB for persistent storage. This is not enough space to run an update.

Update files will be stored on hard drive only after the OS is installed. From a live environment, the HDD is not used at all (ideal situation assumed).

---

