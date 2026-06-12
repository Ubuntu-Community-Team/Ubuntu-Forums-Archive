---
title: "How can I make a usb live cd and save changes to the same usb stick?"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2010-11-26
How can I make a usb live cd and save changes to the same usb stick?

I have the unetbootin program and plan to install ubuntu on my 4 gig flash drive. What do I need to do to save the changes and preferences and even install a few programs to it. I essentially want it to behave the same way as if I had installed it to my hard drive except with a 4 gig memory limit.

---

### Post by C.S.Cameron on 2010-11-26
USB Startup Disk creator that comes with Ubuntu will make a persistent flash drive.

Edit:
If you actually want a persistent Live CD for some reason, format your pendrive ext2 or 3 and name that partition casper-rw, plug it in while booting the Live cd, hit Esc while booting, then F6 and type " persistent", (there should be a space before persistent).

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

If you want less than 4GB persistence, you can get your hands on a casper-rw file, say from pendrivelinux.com, and drop it in the pendrive root directory, then edit syslinux.cfg as above.

---

### Post by sent17inel on 2010-11-26
so I would need a live disk on cd to boot from and then boot up ubuntu and use that program?

---

### Post by sent17inel on 2010-11-26
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

this looks like it will work for me. thank you.

---

### Post by C.S.Cameron on 2010-11-26
That would be the easiest method.

However pendrivelinux.com offers universal USB installer which will make a persistent flash drive while booted from windows.

However I just noticed you said:
> 
I essentially want it to behave the same way as if I had installed it to my hard drive except with a 4 gig memory limit

In which case you can do a Full install to pendrive, 4GB is a little small but step by step for 10.10:

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
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (0 to 1 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
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

### Post by sent17inel on 2010-11-26
> **C.S.Cameron said:**
> That would be the easiest method.

However pendrivelinux.com offers universal USB installer which will make a persistent flash drive while booted from windows.

However I just noticed you said:


In which case you can do a Full install to pendrive, 4GB is a little small but step by step for 10.10:

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
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (0 to 1 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
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

thank you sooooo much!  I have some tinkering to do now.  :o

---

