---
title: "Permanent Install to USB"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by Lolpanda on 2010-06-13
Morning (Or afternoon/evening) Everyone. I've gone through Google, and the Ubuntu COmmunity Wiki's and so far haven't gotten a solid answer to this problem. 

I would like to install _Karmic_ to a USB -- Note: Not make it a live USB to install to another system from, but to actually have it like its own hard drive and have it be no different than the hard drive im on right now, except, ya know, smaller haha.

I'm finding a lot of tutorials for creating LIVE Usb installs, but nothing about a permanent one where all changes would be saved between sessions without a hassle.. Unetbootin's out, Portable Linux is out, The standard USB Start Up Disk Creator is out. 

If anyone knows of a good one, I'd be very appreciative.

---

### Post by confused57 on 2010-06-13
Herman's tutorial should work:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by C.S.Cameron on 2010-06-13
Turn off and unplug the computer.
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
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext4, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning, Ext4, and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

---

### Post by oldfred on 2010-06-13
Herman has another one that is for flash or SSD.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by efflandt on 2010-06-13
Nothing special is needed for full install to a USB drive or flash, EXCEPT you have to pay attention to where you put grub from some hidden options.

After you set up partitions and your user and get to a summary screen, pay attention to the **Advanced** button.  That is where you tell it to put grub on the mbr of the USB drive, instead of default to your main hard drive.  If you fail to do that, you will wonder why you will need your USB drive plugged in to boot anything at all.

This all assumes that you can set your BIOS to boot from USB.  For some computers you may still need to press a key (Esc or F12) during boot to select USB.  Dell laptops often boot so fast that a USB hard drive is not spun up and recognized yet, so somethings that requires either rebooting to get to USB, or changing something in CMOS set up that does not matter (like boot order of floppy or CD/DVD), so it will boot from scratch with the drive already running.

---

