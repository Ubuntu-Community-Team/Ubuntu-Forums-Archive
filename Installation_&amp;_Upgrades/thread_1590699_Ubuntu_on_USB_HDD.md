---
title: "Ubuntu on USB HDD"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by MikePerryUK on 2010-10-08
I would like to install Ubuntu onto a USB hard drive so that it can be used with either of our 4 PCs or taken with me when I visit relatives.  I'd like to have 10.04 initially and then upgrade of 10.10 when the stable version is released.
Anyone know how to get the install done on the USB drive so that the exisiting M$ OS MBR is not altered at all and so that other machines will boot into Ubuntu when the drive is attached (and the BIOS set suitably)?
I want it to be a simple as possible so all I need to do to run Ubuntu is to plug in the USB drive and reboot the machine.  Plus, if the USB drive is not connected then it will boot into the original OS (which may be XP, Vista, W7, etc).
Thanks.

---

### Post by sikander3786 on 2010-10-08
You can install Ubuntu on the USB drive the way you'd normally install it to a HDD. Only on Step 8 during installer, just before clicking Install, click Advanced and select your USB drive as the target for installing Grub.

Disconnecting the internal HDDs is always preffered and a safer approach to minimize the risk of messing up your data. You will be in a bit of trouble if you don't select the correct target for Grub installation.

You can install 10.04 and then upgrade to 10.10 as with the normal install.

You'll definitely need to select your USB HDD from Bios whenever you want to boot into Ubuntu.

When you disconnect your USB HDD, the system should definitely boot into the original OS.

---

### Post by MikePerryUK on 2010-10-08
Thanks for that reply.  Makes sense to disconnect the existing drives so the installer only 'sees' the USB drive.  I'l give it a try and come back if there are any problems.
Thanks

---

### Post by Warlok22 on 2010-10-08
hy there 

steps are easy to follow :

1 .go to [http://www.ubuntu.com/](http://www.ubuntu.com/)
2. in the right corner you'll see in Orange Box DOWNLOAD ... press it !
3. chouse the version that suits you better x86 (32 bits) or X64 
4. after download is finished in the UBUNTU page the second step select USB and click "Show me How"

from there it should be easy enough to figure it out ! 

Hope that this answer suit;s you well !

GL  and HF

---

### Post by sikander3786 on 2010-10-08
> **Warlok22 said:**
> hy there 

steps are easy to follow :

1 .go to [http://www.ubuntu.com/](http://www.ubuntu.com/)
2. in the right corner you'll see in Orange Box DOWNLOAD ... press it !
3. chouse the version that suits you better x86 (32 bits) or X64 
4. after download is finished in the UBUNTU page the second step select USB and click "Show me How"

from there it should be easy enough to figure it out ! 

Hope that this answer suit;s you well !

GL  and HF
It will only create a startup disc as an installation media that won't save your settings, docs etc. The closest thing to that is a USB persistent install however I prefer to do a complete install on my USB drives.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by C.S.Cameron on 2010-10-08
Following is for an 8GB USB HDD or flash drive.
Increase partition size to suit.
First FAT32 partition is  so drive will also work on Windows machine:

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
At boot you will then be given the option to boot your internal hard drive, even when booting another computer.

---

### Post by efflandt on 2010-10-08
Some people apparently missed the OP's words "USB hard drive".

Once you are experienced enough to know where the **Advanced** button in the last step (summary screen) before installation proceeds, to select to put grub on mbr of your USB drive instead of default to mbr your main drive, it is not really necessary to disconnect your internal drive first.  But that is safest to disconnect your internal drive if doing that when new to Ubuntu.

That applies to 10.04 and earlier, not sure if it applies to 10.10, because when I installed 10.10 beta, and used Advanced partitioning to select a partition already created on my USB drive for / (root file system), the installer in beta automatically defaulted to putting grub on the USB drive.  But I only upgraded that to RC (did not install RC from scratch), so not sure if the RC or final 10.10 version will do it intuitively like the beta or use the old method.

I am posting this from 64-bit 10.10 booted from a USB hard drive (WD Passport).

PS: If you intend to boot the USB hard drive on multiple computers, you may want to stick with default video.  For example with proprietary nvidia drivers it still boots to another PC with ATI video, but the nvidia specific glx module interferes with mesa glx. So video may be slower on PC's without the same proprietary video than it would be with default video drivers.

---

