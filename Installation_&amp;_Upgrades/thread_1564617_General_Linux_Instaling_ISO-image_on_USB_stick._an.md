---
title: "General Linux: Instaling ISO-image on USB stick. and boot?"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by bokopperud on 2010-08-30
Is there a *general* way to install an ISO-image on an USB-pen, and boot from it?  I know there is an Ubuntu-utilty to install ISO-image on an USB-pen, and that there is a couple of Windows-programs for making a bootable USB-pen from an ISO-image; but I'm looking for a *general procedure* to make a bootable USB-pen from an ISO-image *under Linux* (that can also be used for other ISOs than Ubuntu)?

---

### Post by C.S.Cameron on 2010-08-31
You can boot isos of many Linux versions using this:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Or you should be able to install most versions to pendrive the same as to internal drive.
(It is safest to disable your internal drive first).
for example:

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

### Post by oldfred on 2010-08-31
I have done both of C.S.Cameron's recommendations. 

I have a 4GB flash with several ISOs. I did it manually but the script for multiboot USB looks like it simplifies it. It is not difficult to do, just format flash to FAT32, install grub2, copy ISO's to a directory and the most difficult part is getting the loop mount command correct in grub.cfg. Script has all that automated.

I also created a full install on a 16GB flash. It is just like a full install but you should change a few settings. See comments during this install procedure for settings.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by Megaptera on 2010-08-31
You may also find this site interesting, dedicated to running Linux portably:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

