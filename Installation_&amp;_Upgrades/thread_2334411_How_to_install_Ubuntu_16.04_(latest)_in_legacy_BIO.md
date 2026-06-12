---
title: "How to install Ubuntu 16.04 (latest) in legacy BIOS mode (no Windows install)"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by ali-ariss on 2016-08-19
This is not a duplicate, I can find nobody answering this question properly on the forum!

I find it frustrating that if I unplug my Ubuntu USB and boot into my Windows SSD, the USB becomes unbootable. I understand this is due to Ubuntu (and the grub bootloader) being formatted for UEFI.
I ask is there a way to install Ubuntu (or perhaps alter it) so it runs on legacy BIOS mode and so eliminates this problem of not being bootable.
**Again: There is no other OS install on the USB: just Ubuntu!**

Please don't be a Microsoft Forum and please directly answer the given question.
Thanks
-Ali :)

---

### Post by grahammechanical on 2016-08-19
Powering off the machine when running Ubuntu from a USB stick will always mess up the format of the USB stick. I have found that out from personal experience. Oh, by the way, I have a BIOS motherboard.

On this forum we do not mind different people asking the same questions that others have already asked. It is only when the same person posts duplicates in different sections of the forum and so wasting our time that we get a bit miffed.

The Ubuntu live session can load in both BIOS/Legacy mode or EFI mode on machines with a UEFI boot system. The situation becomes a bit more complicated if we have installed Ubuntu to a USB drive. Then we have to decide if we are going to install Ubuntu in EFI mode or BIOS/Legacy mode. And that choice will depend on what mode any another OS present has been installed in.

Load the Ubuntu live session in BIOS mode and Ubuntu will be installed in BIOS mode. Load the Ubuntu live session in EFI mode and Ubuntu will be installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sudodus on 2016-08-20
Welcome to the Ubuntu Forums :-)

I can add a few questions and tips to the good introduction by *grahammechanical*.

- Do you want to install Ubuntu into an internal drive or to an external drive? If you want to install it into an internal drive, and it will be the only operating system, you need not worry much. The installer will do its thing.

- It will be a bit more complicated if you want to keep Windows and install Ubuntu alongside Windows.

In both cases I suggest that you *keep a backup or at least recovery disks of Windows* in case you change your mind and want (or need) Windows for certain tasks, or in case something goes wrong, when you try to create a dual boot system. Installing an operating system is a risky operation.

One 'lazy' kind of backup is to unplug the internal drive with Windows and install Ubuntu into a new drive. You can simply keep the original drive as a backup for Windows.

- If you want to run Ubuntu in BIOS mode, fine. After you have backed up Windows, if I manage to convince you ;-), you can install Ubuntu such that it uses the whole drive. Then it will create new partitions and overwrite Windows. If you want to be completely sure, you can boot into a live session 'Try Ubuntu', and start gparted before you start the installer.

In *gparted*, select Device -- Create partition table and create an MSDOS partition table (the default). See this link: [FormatHelp](https://wiki.ubuntu.com/Win32DiskImager/iso2usb/FormatHelp)

After that you can start the installer and install Ubuntu into the whole drive.

-o-

***Edit:*** If you want to keep Windows in the internal drive, and ***install Ubuntu into an external drive***, it is easiest and safest to ***remove the internal drive, before installing Ubuntu***. This will decrease the confusion as well as the risk of damaging Windows.

---

