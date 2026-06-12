---
title: "Space allocation for a 32gb usb installation"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by rchawla8 on 2013-01-23
I want to install ubuntu on a 32gb flash drive, so that I can use it as a live-OS, and use it between different computers. However, I am not sure how to go on doing this, because I have never done a manual Ubuntu installation ( I always use the default settings to write it alongside Windows on my hard drive.) 

I am thinking of one of two methods, either make it a startup-disk with persistence, or installing it using a Live CD on the USB using a manual installation. My question is how much allocation should be necessary  for each method, and which is better. I want to use 12.04 LTS (12.10 is incompatible with my desktop), and also I want to make sure that I do not run out of space quickly. If, for instance, I download 5 gig's of data, and I have only 1gb persistence, would that data be lost after next reboot. How do I make sure this doesn't happen? 

thankyou.

---

### Post by C.S.Cameron on 2013-01-23
A persistent install is limited to 4GB of persistence, unless you use casper-rw and home-rw partitions, these partitions need to be ext filesystem which can't be used by a windows computer.

Following is step by step how to install 12.04 on a 32GB flash drive, partition size can be varied:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
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
Make "New partition size..." about 20 to 24 GB.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2 to 5 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
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

### Post by rchawla8 on 2013-01-23
thanks, I will attempt the method. 

Note, I do not want to use grub (it is a messy procedure to configure with windows 8). After installation, I will choose the usb from BIOS.

---

### Post by Cheesemill on 2013-01-24
You still have to install grub, Ubuntu won't boot without it.

By following the direrections above, however, you are installing grub to the USB drive, not to your hard drive. This way it doesn't affect the Windows boot loader at all, grub is *only* run when your instruct your machine to boot from the USB.

---

