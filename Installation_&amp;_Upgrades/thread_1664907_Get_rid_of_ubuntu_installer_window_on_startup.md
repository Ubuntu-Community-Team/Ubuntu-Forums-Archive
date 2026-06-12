---
title: "Get rid of ubuntu installer window on startup"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by schnecki on 2011-01-11
Hi,

i created an ubuntu 10.10 live system on an usb stick last weekend using the build in startup disk creator. The System itself is working quite fine, but since I don't want to install ubuntu to the computer I'm using the stick with, I want to get rid of the start window (TRY OUT or INSTALL). How can I achieve this?

Thanks,
Jens

---

### Post by wilee-nilee on 2011-01-11
> **schnecki said:**
> Hi,

i created an ubuntu 10.10 live system on an usb stick last weekend using the build in startup disk creator. The System itself is working quite fine, but since I don't want to install ubuntu to the computer I'm using the stick with, I want to get rid of the start window (TRY OUT or INSTALL). How can I achieve this?

Thanks,
Jens

You can't.

---

### Post by schnecki on 2011-01-11
> You can't.

No Problem, then what is the easiest way to create a live system without the window?

---

### Post by wilee-nilee on 2011-01-11
> **schnecki said:**
> No Problem, then what is the easiest way to create a live system without the window?

Your best method is to hold down the shift key immediately upon powering on this will bring up an earlier window I suspect you haven't seen hit try then boot. This is just the way it is with this sort of install.

---

### Post by C.S.Cameron on 2011-01-11
The start window from an UNetbootin install is not near as bad as from an usb-creator install. (Let me know if you wish to make an UNetbootin install persistent).
Better yet do a full install:

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

