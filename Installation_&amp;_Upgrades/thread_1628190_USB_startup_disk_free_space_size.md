---
title: "USB startup disk free space size"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by sites on 2010-11-22
I went to create a startup disk with my new 32GB flash drive & the largest amount of free space I could assign was 4GB.  Is this a limitation I can overcome post-install with gparted, or should I use something other than Startup Disk Creator in Lucid?

---

### Post by sites on 2010-11-22
Found an answer myself, [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

We'll see how it goes......

Well, after trying "Method 0: Automatically create Live USB system", I couldn't access the new partition from a live boot.  It shows up in nautilus but doesn't mount.  The only way to test this would be to try and add a file that's larger than 4GB.  That's what I'm ultimately trying to do here.  I want a partition that isn't FAT so I can add larger files to the free space.

---

### Post by oldfred on 2010-11-22
If you have 32GB why not a full install?

I did a full install to my 16GB flash drive and while a little slower due to flash & USB connection it works reasonably well. I also used grub2 to install to my 4GB flash and have several ISOs on it for loopmount booting. I use that for all installs and have several repair type ISOs also on it.

Full Install:
How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the caveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB)
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by C.S.Cameron on 2010-11-22
Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 12 GB FAT32 partition, (on the left side of the bar). (this partition is for use on a windows computer, size is optional)
Create a 8 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

Adjust partition sizes as required using gparted.

---

### Post by C.S.Cameron on 2010-11-23
> If you have 32GB why not a full install?

This is a good option for a 16GB drive, you can then do updates and upgrades:

Step by step for 10.10:

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
Make "New partition size..." about 12GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 8 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 10 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (2 GB), Beginning and "Use as" = "swap area" then OK.
(Important)
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

### Post by sites on 2011-02-26
Thanks for the tips, guys.  I'll try this out with one of my 16GB drives.

Cheers

---

### Post by Hedgehog1 on 2011-02-26
> **C.S.Cameron said:**
> ...
Create 12 GB FAT32 partition, (on the left side of the bar). (this partition is for use on a windows computer, size is optional)
...

+1 on putting a FAT32 partition so you can transfer windows files as well us boot off the USB stick.

When I showed my 16gig 'Real Pocket PC' to some other engineers at work, they created a name for it I really like:

[SIZE="2"]**Ubuntu-On-A-Stick**[/SIZE]

I hope it catches on.  I makes me smile just to say it.

:KS

---

