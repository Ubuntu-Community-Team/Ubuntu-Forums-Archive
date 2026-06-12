---
title: "Installing Ubuntu 10.04 to USB Drive"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Craigusus on 2010-05-26
Hi all,

Complete novice here so be gentle...

I have installed the ubuntu-10.04-desktop-i386.iso to a USB Key/Drive using Universal USB Installer (v1.5.5).
I restart my machine and boot to Ubuntu from USB.
I then go to System > Administration > Update Manager and download all the updates and start to install them.
I then come across this...

[IMG]http://www.craigfews.co.uk/Images/Screenshot.jpg[/IMG]

Where do I go from here ?
Do I need to type anything in ?

Thanks,

Craig

---

### Post by C.S.Cameron on 2010-05-26
If you want to do updates and upgrades you should do a "Full" install to the flash drive.
Is your iso install even persistent? I mean does it save changes?
I think the iso file is frozen and not easily modified, you can not upgrade the kernel.
You can make a iso install persistent using a persistent partition, (casper-rw) or with a persistence file by the same name.
For a 16 GB flash drive I would suggest the "Full" install.
Disable your internal HDD insert the Live CD, plug in the flash drive and run install after booting.
Use manual partitioning to keep a FAT32 partition as your first partition so you can save stuff to it from a Windows computer.

---

### Post by Craigusus on 2010-05-27
C.S.Cameron,
Thanks for your reply, but maybe I didnt explain myself to well...
I used Universal USB Installer from [PenDriveLinux.com]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and installed it to my USB Drive/Key.
[IMG]http://www.craigfews.co.uk/Images/Untitled.jpg[/IMG]
[IMG]http://www.craigfews.co.uk/Images/Untitled2.jpg[/IMG]
[IMG]http://www.craigfews.co.uk/Images/Untitled3.jpg[/IMG]

Once finished this is what is on the USB Drive...
[IMG]http://www.craigfews.co.uk/Images/Untitled4.jpg[/IMG]

Then restarted and booted from USB on my PC.
There is/was no need to disconnect my hard drive(s).

---

### Post by C.S.Cameron on 2010-05-27
You have done a persistent disk image install.
You now have 4GB of persistence. Space in which to save stuff.
You will use this up very quickly if you start doing updates or try upgrading.
It is better to use the space for installing new applications and customizing the install.
If you feel you need to update or upgrade then do a Full install.

In answer to your original question I don't think you need to type anything in.

---

### Post by Arsic on 2010-07-14
Came across this application too. I have a 16GB USB drive that I want to use for the full install. This application only let's you have 4GB max persistence.

---

### Post by Craigusus on 2010-07-14
@Arsic,

In the end I went and followed C.S.Cameron's post and did a full install onto my USB:

> **C.S.Cameron said:**
> If you want to do updates and upgrades you should do a "Full" install to the flash drive.
Is your iso install even persistent? I mean does it save changes?
I think the iso file is frozen and not easily modified, you can not upgrade the kernel.
You can make a iso install persistent using a persistent partition, (casper-rw) or with a persistence file by the same name.
For a 16 GB flash drive I would suggest the "Full" install.
Disable your internal HDD insert the Live CD, plug in the flash drive and run install after booting.
Use manual partitioning to keep a FAT32 partition as your first partition so you can save stuff to it from a Windows computer.

Physically disconnected my HDD, plugged in my USB Drive then booted from the LiveCD and installed from there...

P.S. @C.S.Cameron, sorry for the non-reply. Thank you for your assistance!

---

### Post by C.S.Cameron on 2010-07-14
Step by step Full install:

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

### Post by Pumalite on 2010-07-14
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by BananaPeal on 2011-02-17
Good Evening Mr. Cameron,

Could you help me straighten out a grub2 problem?

I've followed your step-by-step instructions with the omission of the swap file. I've even unplugged the hdds while doing so. I also checked that "bootloader" was getting installed to /dev/sda (which is usb since no other drives attached)

When I tried to restart it with the hdds still unattached, I get hdd error message.
With hdd attached, boot hangs after "checking dmi pool data"

What should I do now? Is there a way to check what grub wrote to the mbr? I'm pretty sure the grub files made it into the /boot folder ok tho i can check those easily with liveCD.

Thanks for your time, I hope I can get this to work, portable linux is a dream of mine!

---

