---
title: "Installing 10.04 onto USB Flash Drive"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by petitalastair on 2010-07-08
Right now, I'm trying to install Ubuntu 10.04 onto my 8GB flash drive using [these instructions]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Method 1: Installing Ubuntu directly to USB drive from installer CD"). I've run the install and installed GRUB2 and 10.04. However, selecting 10.04 on GRUB doesn't work.

On the instructions, it says this:
> You will also need to manually edit the menu.lst file of the new USB installation to change the boot references to /dev/sda, rather than /dev/sdb (or /dev/sdc etc.). This can be done by booting to the live distro mode of the Ubuntu install CD and editing the /boot/grub/menu.lst file on the USB stick. You can mount the USB stick using the Places menu -- once mounted, it can be found at /media/disk.

I'm not sure what the equivalent step would be for the GRUB2 files.

Thanks. :)

---

### Post by BbUiDgZ on 2010-07-08
> **petitalastair said:**
> Right now, I'm trying to install Ubuntu 10.04 onto my 8GB flash drive using [these instructions]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Method 1: Installing Ubuntu directly to USB drive from installer CD"). I've run the install and installed GRUB2 and 10.04. However, selecting 10.04 on GRUB doesn't work.

On the instructions, it says this:


I'm not sure what the equivalent step would be for the GRUB2 files.

Thanks. :)

i don't have an answer for you but you might want to read [this](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by oldfred on 2010-07-08
I used a USB flash drive to install to a larger USB flash drive. The only issue I had was after removing the install flash drive the new install became a different drive. 

I had to manually edit the set root = line to be the correct (new) drive number. Because I default boot from sdc my system also numbers drives differently. The boot drive (sdc) is hd0 and then the drives corespond to remaining letters & numbers ie sda is hd1 etc.

At grub menu use e to edit and change hdX,Y to correct number. You may have to experiment to find what grub thinks the correct number is.

---

### Post by C.S.Cameron on 2010-07-08
I think that page is old.
If you are doing a Full install you can't go wrong disabling the internal HDD before proceeding.

Following is how I do it:

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
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1).
At boot you will then be given the option to boot the hard drive.
Grub does not end up as clean as when disabling the HDD.

---

### Post by Nick_Jinn on 2010-07-08
Installing to flash drive has been easy for me.

Getting it to boot from flash drive when I plop it into a computer at school has not always been successful.

---

### Post by petitalastair on 2010-07-13
> **C.S.Cameron said:**
> I think that page is old.
If you are doing a Full install you can't go wrong disabling the internal HDD before proceeding.

Following is how I do it:

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
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1).
At boot you will then be given the option to boot the hard drive.
Grub does not end up as clean as when disabling the HDD.

How do you unplug it? It's a multi-colour cable with a white cap, right? I don't want to yank too hard and accidentally break it.

---

### Post by cr4321 on 2010-07-13
Why not just use the Startup Disk Creator in the Systems/Administration Menu?

---

### Post by C.S.Cameron on 2010-07-13
If it is an IDE hard drive there should be three, (or four), wires, red, black, or yellow. with a four pin white cap.

see here:

[http://tech-help.info/sitebuilder/images/IDE_Hard-drive_with_IDE_and_Power_cable_crop-600x485.jpg](http://tech-help.info/sitebuilder/images/IDE_Hard-drive_with_IDE_and_Power_cable_crop-600x485.jpg)

---

### Post by petitalastair on 2010-07-13
> **C.S.Cameron said:**
> If it is an IDE hard drive there should be three, (or four), wires, red, black, or yellow. with a four pin white cap.

see here:

[http://tech-help.info/sitebuilder/images/IDE_Hard-drive_with_IDE_and_Power_cable_crop-600x485.jpg](http://tech-help.info/sitebuilder/images/IDE_Hard-drive_with_IDE_and_Power_cable_crop-600x485.jpg)

Yep. That's it. So I just pull on it and it should come out?

---

### Post by petitalastair on 2010-07-13
> **cr4321 said:**
> Why not just use the Startup Disk Creator in the Systems/Administration Menu?
That creates a Live USB.

---

### Post by C.S.Cameron on 2010-07-13
> Yep. That's it. So I just pull on it and it should come out?

Hold it the by white part and maybe wiggle it a bit, don't yank on the wires.

---

### Post by petitalastair on 2010-07-13
Well, I figured out how to get it work and I actually didn't need to unplug the hard drive. I just selected to install GRUB on /dev/sdb instead of /dev/sdb1 and that did the trick. Now I know how to unplug my hard drive now, though. (Thanks, C.S.Cameron.)

---

### Post by C.S.Cameron on 2010-07-13
Make sure you don't have grub problems when using the drive on other computers, it may try to find drives that aren't there when booting.
It should still work though.

---

### Post by Nick_Jinn on 2010-07-14
I used the startup disk creator, but when I reboot it doesnt show that second version of Ubuntu as an option at Reboot.

---

### Post by C.S.Cameron on 2010-07-14
> **Nick_Jinn said:**
> I used the startup disk creator, but when I reboot it doesnt show that second version of Ubuntu as an option at Reboot.

Is your BIOS set to see the flash drive as the first hard drive?

---

