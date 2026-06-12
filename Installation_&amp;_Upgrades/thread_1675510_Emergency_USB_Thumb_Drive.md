---
title: "Emergency USB Thumb Drive"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by jmoe816 on 2011-01-25
Hi, my issue may be hard to explain but I'll try.
 
I want a USB drive for emergency situations. It will have sensitive information, family photos, etc. stored on it. I want it to have one encrypted portion (TrueCrypt) for the sensitive materials. I want the files to be able to be viewed on a Windows machine first and foremost. If no Windows machine is available I would like to have a bootable version of Ubuntu on the USB drive so I can boot it and also view the files. 
 
Is this possible? Thanks.

---

### Post by C.S.Cameron on 2011-01-25
Following is a step by step for Full install of 10.10 to USB drive.
The first partition will be available to Windows, (Windows only sees the first partition on a flash drive). You can make the first partition FAT32 for a flash drive or NTFS for a USB HDD.
Adjust partition size to suit.

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

### Post by Megaptera on 2011-01-26
If you install Ubuntu on a thumb drive it'll erase what's on there already so make sure you backup elsewhere first anything you don't want to get wiped.

---

