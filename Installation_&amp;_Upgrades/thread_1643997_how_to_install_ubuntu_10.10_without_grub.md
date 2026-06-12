---
title: "how to install ubuntu 10.10 without grub?"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by zero1one0 on 2010-12-12
Hi, I installed ubuntu 10.10 on my usb key.  But grub has been causing me some issues because as you can imagine I absolutely need my usb to boot into win7 even though in the installation of ubuntu i told it to install the boot loader on the hard drive.

I want to reinstall it without installed grub at all.  I am going to restage my win 7 computer so my mbr will be like brand new, but when I reinstall ubuntu 10.10 onto my usb key i do not wish for it to install grub.
Is there any way to do this?

---

### Post by C.S.Cameron on 2010-12-12
Here is a thread discussing the same problem, lilo fixed the Windows MBR:

[http://ubuntuforums.org/showthread.php?t=1643330](http://ubuntuforums.org/showthread.php?t=1643330)

You need to install grub for the flash drive to boot to work, only it needs to be installed on the flash drive.
Best solution is to unplug the internal HDD.

Following step by step usually works:

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
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by zero1one0 on 2010-12-15
Thank you for such an in depth explanation.
I will attempt this the first time I get the chance and I will  let you know how it goes.
Thanks again.

---

