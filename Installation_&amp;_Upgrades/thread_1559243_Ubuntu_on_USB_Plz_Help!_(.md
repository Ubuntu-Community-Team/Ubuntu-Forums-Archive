---
title: "Ubuntu on USB Plz Help! :("
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Velua on 2010-08-23
Hey

first off thanks for reading this :)

I would like to sorta copy my Ubuntu on to a USB bootable to go into ubuntu,

Now I know you can do that with like a LiveCD into a LiveUSB sorta thing, and it holds files and all that

But I want the real kinda Ubuntu on the USB, One that will also install everything and act exactly like it was installed on the hardrive, Is that possible?

Because if it is it would be amazing :D haha 

and even more if I could copy over my existing Ubuntu on to the USB so I have 2 the exact same but thats probably pushing it,

Main question pretty much
I know you can get a bootable Ubuntu USB, But the one I have act's like its just to show off

I want Ubuntu on a USB which will do anything that it would on a hardrive 

Sorry if I havent really worded this properly im really bad :S

Thanks alot for reading!
and even more if I get a reply :)
Thanks. :D

---

### Post by arubislander on 2010-08-23
Hi, and welcome.

As I understand it, the reason for having a LiveUSB with persistence is to avoid wearing out your USB stick by writing to the same place on the stick's memory too often.

It is possible to install Ubuntu to a USB stick as to any other USB block device (like an external drive), but then you won't have the benefit of the above mentioned protection scheme.

---

### Post by C.S.Cameron on 2010-08-23
A typical flash drive is good for over 10000 writes.
If you do the math a 16GB drive will last several years writing continuously.

To make a Full install flash drive:
Turn off and unplug the computer. (See note at bottom)
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
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

