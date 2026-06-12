---
title: "Running Mint (full version) from Flashdrive, can it be done?"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by dkdias on 2010-12-12
I would like to run Linux Mint fullversion from a flashdrive. Is it possible and easy to set up. I have found how to basically create a flashdrive version of the live cd, but I would like to run the full version from the flashdrive.  Can someone give me step by step instruction on how to do this.  I am fairly new to to linux so please be gentle... :)

---

### Post by snowpine on 2010-12-12
I would recommend asking on the forums over at [http://linuxmint.com](http://linuxmint.com) 

I assume it can be done, since it is easy with Ubuntu (using the application "usb-creator" and choosing the Persistent option) and Mint is somewhat based on Ubuntu. :)

---

### Post by oldfred on 2010-12-12
snowpine's is the USB installer but it is running the ISO version with persistence.

If your flash drive is 8GB or larger you can do a full install and it is just like any install to a second or external drive. But you have to be careful to make sure grub2 installs to the flash drive during the install and not to your internal drive. Grub like to default to sda and with Maverick only gives you a choice if you use manual install.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB)
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

Some settings for better flash drive performance:
Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

I would recommend partitioning the flash drive in advance and then using manual install, so you get the option of which MBR to install grub to.

---

### Post by dkdias on 2010-12-12
> **oldfred said:**
> snowpine's is the USB installer but it is running the ISO version with persistence.

If your flash drive is 8GB or larger you can do a full install and it is just like any install to a second or external drive. But you have to be careful to make sure grub2 installs to the flash drive during the install and not to your internal drive. Grub like to default to sda and with Maverick only gives you a choice if you use manual install.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB)
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

Some settings for better flash drive performance:
Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

I would recommend partitioning the flash drive in advance and then using manual install, so you get the option of which MBR to install grub to.
Thank you for your information. The flash drive I was planning on using was an 8 GB. I will check out the links you gave me to find the step by step instruction!

---

### Post by C.S.Cameron on 2010-12-12
I understand that mint is a mod of Ubuntu and that the install method is similar.
Following is step by step for 10.10, (the page Oldfred refers to is for 10.04).

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
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by efflandt on 2010-12-13
One issue I ran across with in earlier Mint version is that it used /dev paths in /etc/fstab instead of UUID's.  That can be a problem for a USB device, especially if you use iso on USB to install it or different computers with different number of drives.

For example if you have one internal drive and use iso on USB to install to USB, that might be /dev/sdc1 during install, but /dev/sdb1 when you try to boot it.  If that is an issue you can fix that from live CD or iso on USB.

---

### Post by dkdias on 2010-12-13
Wow thank you for the step by step!! :-)

---

### Post by dkdias on 2010-12-19
Thank you everyone for your help!!  I got it done just a little bit ago.  This was a Christmas gift to my brother in law so that he could play with Linxu Mint

---

