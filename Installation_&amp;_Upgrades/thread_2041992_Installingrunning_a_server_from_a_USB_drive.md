---
title: "Installing/running a server from a USB drive"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by Dubslow on 2012-08-13
For reasons that aren't relevant, I have a box which needs to be turned into a web server but doesn't have a hard drive. "Okay, we'll just run it off the live disk." (A flash drive, to be clear.) So I DL'd Server 12.04 and created the startup disc from my desktop's GUI "Startup Disk Creator". I plugged in the flash drive, it booted fine, and I chose install. It seemed to be going fine until it asked me to setup the partitions, except it doesn't present me any.
```
Configure iSCSI volumes

Undo changes to partitions
Finish partitioning and write changes to disk
```
The blank entry does nothing (as expected). I don't see the USB flash drive itself appearing.

That seems to suggest to me that I shouldn't be choosing the install option at the initial menu, but this "installation" will be running full time from the flash drive (it has been dedicated to this purpose). I did make the startup disk persistent, but ideally I should be able to boot the computer without having to select "Run Ubuntu Live Disk" (as opposed to the install option) and login every time, since as a server it won't be physically attached to a screen.

What's the best course of action?

---

### Post by Cheesehead on 2012-08-13
> **Dubslow said:**
> "Okay, we'll just run it off the live disk." (A flash drive, to be clear.)
...
I plugged in the flash drive, it booted fine, and I chose install.
Since there is no disk to install to, you probably shouldn't choose 'install'. You said you want to run it from the USB...which seems like exactly what you *were* doing.

Instead, stay in the Live environment, open a terminal, and start working.

---

### Post by C.S.Cameron on 2012-08-14
Following is step by step how to install 12.04 on a 8GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD, or USB.
Start the computer, the CD, or USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 bytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 bytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 bytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 bytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by Dubslow on 2012-08-14
> **Cheesehead said:**
> Since there is no disk to install to, you probably shouldn't choose 'install'. You said you want to run it from the USB...which seems like exactly what you *were* doing.

Instead, stay in the Live environment, open a terminal, and start working.
Yes, but that means every time I boot I have to plug in a keyboard and screen and select "Run live disk" from the initial menu. It should be able to boot without me needing to interfere.

@C.S. Cameron: Like I said in the OP, there isn't a harddrive in this server. Hence the need to run it from a flash drive. However, you do make a good point that using any other computer I can install a live disk to a USB partition, I think I'll do that. (Why are the instructions so long? It's not that hard to create a partition table. And why, if this is a server, would I ever want Windows within ten feet of it?)

---

### Post by efflandt on 2012-08-14
You can use bootable live/install iso on one USB device to do a regular install to another USB device.  That is basically what I did on my tablet PC, from USB memory stick to internally USB connected SDHC card.  It is just that an actual system will require more space (8 GB minimum recommended) vs. 700 MB + persistent data (casper-rw) for live/install iso.

Something to note is that you cannot update the kernel or anything else that loads during boot from the fixed squashfs file system of an iso. But with a regular system on USB, you can do any updates, video drivers, etc.

---

### Post by C.S.Cameron on 2012-08-14
> **Dubslow said:**
> 

@C.S. Cameron: Like I said in the OP, there isn't a harddrive in this server. Hence the need to run it from a flash drive. However, you do make a good point that using any other computer I can install a live disk to a USB partition, I think I'll do that. (Why are the instructions so long? It's not that hard to create a partition table. And why, if this is a server, would I ever want Windows within ten feet of it?)

The instructions are meant to suit a variety uses, (not just servers) and every mouse click is listed, sorry.
You can build the flash drive on another computer as long as you do not install proprietary drivers.

---

