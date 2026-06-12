---
title: "Instal from HDD"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Stardock on 2010-12-05
Hi all, Linux dummy so be kind please.

A while back I installed the Netbook remix on a netbook and was very happy with the result. It installed like a dream from USB with some simple research. Now I want to instal Ubuntu onto an old lap top I have, a Dell Latitude.

Problem is that the Dell doesn't boot from USB and all the instructions I can find are about burning cd/dvd's or formatting USB sticks. I even tried a couple of the USB stick programs but none recognize the laptop hard drive as a USB stick (obviously)

I am working on a Win 7 machine with the laptop HDD connect by USB with a USB to ATA/Atapi bridge cable "thingy". It sees the drive fine, I use this cable all the time, but it sees it as a HDD not a USB stick.

So how do I format the drive etc so that it will boot up and start the Ubuntu instal from the HDD when I put it back in the laptop?

Thanks in advance

Brendan

---

### Post by Stardock on 2010-12-06
Surely some one can tell me how to instal from a HDD, I can't be the only person with no CD/DVD or USB boot can I?

---

### Post by C.S.Cameron on 2010-12-06
Following is for a USB drive but it should work for you, adjust partition sizes as desired.

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

### Post by Stardock on 2010-12-06
Thanks for the help but sadly that isn't what I need.
That would instal it on the HDD for the computer with a CD.
I need to use the good laptop to make the external hard drive bootable and put the instal files on it, then put that hard drive in the old laptop and have it instal on that laptop.

---

### Post by C.S.Cameron on 2010-12-06
> **Stardock said:**
> Thanks for the help but sadly that isn't what I need.
That would instal it on the HDD for the computer with a CD.
I need to use the good laptop to make the external hard drive bootable and put the instal files on it, then put that hard drive in the old laptop and have it instal on that laptop.

Yes that is the idea.
When you boot the CD and run install it should see the laptop HDD that is hooked up with cables and be able to install to it.
It is a precaution disabling the internal drive but not necessary as long as you confirm that the laptop hdd is the one you are installing to and the one grub is going on.

---

