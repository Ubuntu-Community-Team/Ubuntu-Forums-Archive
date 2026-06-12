---
title: "How to create USB install drive with latest updates?"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by medicdave on 2011-03-17
Hi Everyone-

I'm going to be doing some field testing of Ubuntu for compatibility on various laptops. I'd like to have a USB stick containing the latest kernel, drivers, packages, etc. I already have one prepared with the 10.10 release, but there have been many updates since then and no 10.10.1 release thus far.

Is it possible to update my existing flash drive to the latest and greatest...

[LIST]
[*]...using the software update tool while booted using the drive?
[*]...from within an existing Ubuntu 10.10 installation?
[*]...manually?
[/LIST]

Thanks,
[medic]Dave

---

### Post by mörgæs on 2011-03-17
You could take a look at Remastersys.

---

### Post by dabl on 2011-03-17
Why not use the 11.04 daily build Live CD?  That's about as updated as you can get.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by C.S.Cameron on 2011-03-17
A Full install should do what you want, following step by step for 4GB flash drive, adjust partition size to suit:

Check MD5SUM of the Ubuntu iso file.
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
Make "New partition size..." about 400MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.77GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 600MB, Beginning, Ext2, and Mount point = "/home" then OK.
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

### Post by mörgæs on 2011-03-17
> **dabl said:**
> Why not use the 11.04 daily build Live CD?  That's about as updated as you can get.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The daily build is updated, but it is nevertheless an alpha. If original poster wants something stable, it is better to build on 10.04 or 10.10.

---

### Post by C.S.Cameron on 2011-03-17
If you do a Full install, you can upgrade when 11.04 is released.

---

### Post by dabl on 2011-03-17
However, if you do a full installation, it will be configured for _the specific computer on which the installation is performed_.  That is contrary to the stated purpose of doing field testing, for suitability on a variety of laptops.  You really want a "Live CD" environment, which is optimized to perform on as many hardware configurations as possible.

mörgæs is correct regarding the current Alpha status of 11.04, and its performance may or may not be stellar at this moment.  However, it will be released in about 4 weeks, so if your goal is to make a decision at a future point in time, then the logical released version to consider, at that time, will be 11.04.

---

### Post by C.S.Cameron on 2011-03-18
> **dabl said:**
> However, if you do a full installation, it will be configured for _the specific computer on which the installation is performed_.  That is contrary to the stated purpose of doing field testing, for suitability on a variety of laptops.  You really want a "Live CD" environment, which is optimized to perform on as many hardware configurations as possible.

mörgæs is correct regarding the current Alpha status of 11.04, and its performance may or may not be stellar at this moment.  However, it will be released in about 4 weeks, so if your goal is to make a decision at a future point in time, then the logical released version to consider, at that time, will be 11.04.

My Full installs always work on any computer that I plug them into, (That boot flash.
The only time I have had problems booting multiple computers is after installing proprietary video drivers.

---

