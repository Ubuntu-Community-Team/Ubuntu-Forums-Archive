---
title: "is it possible to install entire OS on usb"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by djbenny on 2012-09-02
i have a usb 2.0 external hard drive 500gb

i was wondering if it were possible to install and run the OS to the drive the same was as to install to internal hard drive? but not as a live disk..as a full install

---

### Post by arpanaut on 2012-09-02
Yes it is possible.
The key is to make sure you install grub into the usb drive and use BIOS to choose the drive to boot.
Say that your usb drive is identified as sde install grub to the mbr of that drive, not one of the partitions of that drive.

Check out the links in this post: [http://ubuntuforums.org/showpost.php?p=12173834&postcount=3](http://ubuntuforums.org/showpost.php?p=12173834&postcount=3)
The rest of that thread gives some good info too.

---

### Post by C.S.Cameron on 2012-09-02
Following is step by step how to install 12.04 on a 8GB flash drive:

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
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
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

### Post by djbenny on 2012-09-03
ok sounds do-able.

but running through usb i presume there will be a performance lag?

---

### Post by mastablasta on 2012-09-03
depends what USB port you have (verison ) and how fast the external drive is.

---

### Post by djbenny on 2012-09-03
well the hard drive is a standard 7200rpm usb 2.0 drive.. connected through a usb 3.0 port on my computer

---

### Post by C.S.Cameron on 2012-09-03
I have not been able to get Ubuntu to boot from USB3 yet.

---

