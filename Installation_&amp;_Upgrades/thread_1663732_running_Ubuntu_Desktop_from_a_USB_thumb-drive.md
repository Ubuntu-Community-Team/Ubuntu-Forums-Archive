---
title: "running Ubuntu Desktop from a USB thumb-drive"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by DavidVS on 2011-01-10
Hi!

I am happy using Ubuntu on my laptop, as a fairly newbie user.

Next, I want to put Ubuntu on my 16 gb USB thumb-drive so that I can use Ubuntu on any computer willing to boot from a USB drive (at my office, my wife's desktop, etc.)

I cannot find how to do this.  All my search attempts show me how to put an "install disk" onto the USB thumb-drive using the command:
  System -> Administration -> Startup Disk Creator

[I]Tangential story... I tried the above.  The first time I booted from the thumb-drive it asked me whether I wanted to try using Ubuntu from the thumb-drive or install.  Having to make that selection with each boot would be a slight pain, but not a deal-breaker.  But then the thumb-drive OS detected my laptop's wireless card, asked to install a driver, and then asked to reboot.  Now it does some odd blended boot where it skips my hard drive's Grub Loader (so it *is* still booting off the thumb-drive) but goes to my hard drive's account sign-in.  Strange!
[/I]
[B]So... How can I make a USB thumb-drive that boots Ubuntu Desktop just as a normal hard drive, with accounts and the ability to install drivers and new software?
[/B]
Thanks for your help,
 David V.S.

---

### Post by C.S.Cameron on 2011-01-10
Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

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

