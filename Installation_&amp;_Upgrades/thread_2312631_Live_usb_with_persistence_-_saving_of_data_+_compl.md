---
title: "Live usb with persistence - saving of data + complete install on a USB"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by Kotseto on 2016-02-05
1.Hi all, I am running a live usb Ubuntu 15 latest version, 64bit  on Sony Vaio with UEFI , created with universal pendrive which allowed to allocate only 4G with persistence for casper.

As I do not want to  run dual boot with win 8 and not yet ready to replace it once & for all ( hopefully you guys will convince me),  is there any reasonable way to save the session of the currently 

installed updates, applications and data alltogether like a New Recovery back up  USB or on an external flash drive and re-run if necessary? I really need that.

2. I read I can install ubuntu on the usb itself , having +10G drive  without messing with other OS and installing Grub & everything on the flash drive.

Would someone give a newbies self-explanatory step-by-step guide to install the whole OS on a USB flash drive w/o messing with other OS and drives.
 

10x
PS: separate questions if better. I already read about the 2nd one but haven't found a neat explanation.

---

### Post by sudodus on 2016-02-06
Welcome to the Ubuntu Forums :-)

> **Kotseto said:**
> 1.Hi all, I am running a live usb Ubuntu 15 latest version, 64bit  on Sony Vaio with UEFI , created with universal pendrive which allowed to allocate only 4G with persistence for casper.

As I do not want to  run dual boot with win 8 and not yet ready to replace it once & for all ( hopefully you guys will convince me),  is there any reasonable way to save the session of the currently 

installed updates, applications and data alltogether like a New Recovery back up  USB or on an external flash drive and re-run if necessary? I really need that.

You could 'convert' the casper-rw file to a casper-rw partition:

Get a new USB pendrive that is big enough, say at least 16 GB, [a ***fast*** USB 3 pendrive](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed), if possible.

Create a persistent live system with a casper-rw partition. You can use the tool [mkusb](https://help.ubuntu.com/community/mkusb).

Boot into a live-only session (without using persistence).

Loop mount the casper-rw file. Mount the casper-rw partition.

Copy the whole file system in the casper-rw file into the casper-rw partition. You can use ***sudo rsync*** to do it. See ```
man rsync
```

Maybe you find it easier to create a fresh persistent live system with a casper-rw partition and to install everything again. Use the method that you find easier :-)
> 
2. I read I can install ubuntu on the usb itself , having +10G drive  without messing with other OS and installing Grub & everything on the flash drive.

Would someone give a newbies self-explanatory step-by-step guide to install the whole OS on a USB flash drive w/o messing with other OS and drives.
 

10x
PS: separate questions if better. I already read about the 2nd one but haven't found a neat explanation.

You can create a system with an installed system in a USB pendrive according to the following link

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

See posts [#8](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506) and [#63](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191).

---

### Post by C.S.Cameron on 2016-02-06
If you require more than 4GB of persistence, you can add an ext2, 3, or 4 partition using gparted and label it casper-rw, (using gparted live).

You can then copy the casper-rw file and mount it someplace convenient:

```
sudo mount -o loop /home/cscameron/Desktop/casper-rw /home/cscameron/Desktop/casper

```
and then rsync it's contents to the new partition.

```
sudo rsync -rltDvu --progress --delete /home/cscameron/Desktop/casper/ /media/cscameron/casper-rw

```
After confirming that the partition is working, you can delete the casper-rw file or save it off root.

This only seems to currently be working with Startup Disk Creator / UNetbootin 32 bit installs.
If you require 64 bit you can create persistent partitions with grub2/iso, (Multiboot type), installs.


Following is step by step how to install 15.10 on a 16GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "+".
Select "Primary".
Make "Size..." about 2000 MB.
Location = Beginning of this space.cscameron
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "+".
Select "Primary", "Size ..." = 4500 to 6000 MB, Beginning of this space, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "+".
Select "Primary", "New partition size ..." = 1000 to 6000 MB, Beginning of this space, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)

Click "free space" and then "+".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning of this space and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, computer name, username, password and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

