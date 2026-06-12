---
title: "Installation on an USB disk"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by AlfaOmega08 on 2010-06-20
I prepared an usb disk using the tool provided with ubuntu. The iso was Ubuntu 10.04 desktop (32bit). I set it up with persistency with 4Gb of space as this usb disk i 16Gb wide. The boot however takes about 25 minutes!!! It is incredibly slow. I would like to install ubuntu on the usb key, without the squashfs file. I'd like to see /bin /home /dev /usr etc etc on the key, without need to umpack the squashfs file on each boot. Is this possible? If not, do you have any idea of why my boot is so slow?

I have a core i7 with 4Gb of ram.

---

### Post by darkod on 2010-06-20
I'm not sure how persistency works, if it tries to load it somewhere I guess, 4GB is lot to load.

Copying 4GB to your hdd takes 12-13mins.

You can install to the stick as destination, just make sure in the last screen of the installer to click on the Advanced button and tell grub2 to install to the stick too. Otherwise if grub2 goes to the int hdd mbr, you won't be able to boot anything without the usb stick plugged.

---

### Post by C.S.Cameron on 2010-06-20
25 minutes sounds like a lot more than I am used to.
Maybe it will become faster after a few boots.
In my experience both Persistent and Full take about the same amount of time to boot.
Following is how I do a full install:
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

As Darko says you can leave your Internal HDD plugged in if you use the Advanced button to apply grub to the correct disk. Even if you overwrite Windows mbr it is fixable.

---

