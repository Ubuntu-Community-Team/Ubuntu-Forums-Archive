---
title: "Kubuntu karmic Live USB to lucid"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by seadx6 on 2011-04-02
Hi I want know how upgrade Mi Kubuntu 9.10 karmic kohala Live USB to the 10.04 lucid lynx this is posible? if this is unposible how can I make a full install of it with not pulling my IDE / SATA cables and detect my USB as hard drive?


Mi USB is a 8GB Kingston DT 101 G2 urDrive

---

### Post by C.S.Cameron on 2011-04-02
Welcome to the forums.

Boot your USB drive, go to system/administration/update manager and you should see an option to upgrade.

Step by step for installing 10.04 to USB follows, if you don't want to disable the hard drive make sure you put the boot loader on the usb drive as noted.

Turn off and unplug the computer. (**See note at bottom**)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
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
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you **select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to**, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by seadx6 on 2011-04-04
Theanks unfortunaly I have not idea for how pull out all I have installed it and GRUB has crashed :( I have reinstalled the HD Kubuntu it is installing now on home

How can I boot Kubuntu from my USB with not GRUB?


             Theanks

---

### Post by C.S.Cameron on 2011-04-05
Use startup disk creator from the Live USB or you can extract usb-creator for Windows from the iso.

---

