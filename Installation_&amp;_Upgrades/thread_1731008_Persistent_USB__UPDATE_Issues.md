---
title: "Persistent USB | UPDATE Issues"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by cold.nut on 2011-04-16
```
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com maverick Release 
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get update
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com maverick Release 
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Reading package lists... Done

```I get that feedback every time I run "sudo apt-get update". I used Pendrive Linux Universal USB installer to create a Persistent Ubuntu USB drive. My goal is to get it updated and have all the drivers installed and updated so I can change to the Macbuntu theme. I seem to be having issues with that theme installing correctly.

Here is what I get when I try to Activate the Broadcom card on the laptop as well.
[[IMG]http://img850.imageshack.us/img850/2818/broadcomerror.png[/IMG]]("http://img850.imageshack.us/i/broadcomerror.png/")

I have tried multiple systems and multiple internet connections thinking that it may be a firewall causing an issue or security measures.. I am very unfamiliar with Ubuntu being ran Live.

---

### Post by C.S.Cameron on 2011-04-16
The files in a persistent install are part of a squash file, it can not be easily updated, trying to do so will quickly fill the casper-rw file, max size is 4GB. once full the drive will no longer boot.
If you want a pendrive install that is updatable and upgradeable do a Full install.
Following step by step for Full install of 10.10 to USB device, partition sizes given are for 8GB drive, adjust size to suit:

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
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

