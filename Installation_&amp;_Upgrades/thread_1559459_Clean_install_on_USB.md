---
title: "Clean install on USB?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by soulfray on 2010-08-23
Hey guys!
Got a question here...
Is it possible to install Ubuntu on a USB Stick [8gb] and boot it then? I mean, not just to try Ubuntu from the pendrive, I want to keep settings and files on it.

---

### Post by McNils on 2010-08-23
yes, you can. But you must be careful with partitioning (manual) and grub installation.

You must be make sure that you install grub on the USB drive. On stage 6, I think, click on the advanced button and select the correct device. If you install it on first hard drive you must have the stick in the computer to boot it.

---

### Post by C.S.Cameron on 2010-08-23
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

### Post by soulfray on 2010-08-23
Thank you both for the fast replies!
I'm ready, so later I will post here whats going on :)

---

### Post by soulfray on 2010-08-23
Hey, I have successfully installed Ubuntu on my usb stick, without having any problems, which is great!
But it's running _kinda_ slowly, is that normal for a usb flash drive? Obviously, the live CD/USB is running times faster ;o

---

### Post by C.S.Cameron on 2010-08-23
It may get a little faster with time.
Now if you can wait for USB3 it should make things a lot faster

---

### Post by soulfray on 2010-08-23
Yea, probably a lot of things will change ;d
Well, thank you for helping me :) Even slower its usable :P

---

### Post by oldfred on 2010-08-23
While USB flash will be slower a few settings may help a little. More info in this link:

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

