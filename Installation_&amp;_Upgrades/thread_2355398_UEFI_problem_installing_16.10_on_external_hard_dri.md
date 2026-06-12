---
title: "UEFI problem installing 16.10 on external hard drive"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by mark allyn on 2017-03-12
Hello all,

I have a 64-bit HP-Compaq desktop which has Windows 7 installed and ALONGSIDE it is installed Ubuntu 12.04.  They live together happily on a 500 M SATA hard drive.

What I'm trying to do is to preserve the existing internal disk setup and install Ubuntu 16.10 from an OSDisc.com DVD in a 1 TB Seagate external EXTERNAL hard drive.  However, I run into the following message:

[HTML]
Force UEFI Installation?     This machines's  firmware has started   this installer in UEFI mode but it looks like there maybe existing   operating systems already installed using BIOS compatibility mode, If   you continue to install Debian in UEFI mode,it might be difficult to   reboot into any BIOS-mode operating system.
[/HTML]

I'm new  to this message.  On previous external hard drive installs, even 14.04 64-bit, this message didn't show up.  It appears to be new with Ubuntu 16+.

I have tried going to the boot screens (using F10 during boot-up) but none of the tabs gives a clear indication of how to boot in BIOS mode rather than UEFI.  It is possible that I am not recognizing the BIOS option because the wording is crytpic.  Or, maybe there is no way to boot in BIOS mode on an HP box?

I'm at the point of simply clobbering the dual mode internal hard drive setup with an installation of Ubuntu 16.10, but thought I'd try this forum before such a drastic step.

Thanks,

Mark Allyn

---

### Post by ubfan1 on 2017-03-12
The Ubuntu install media will boot in either legacy or UEFI mode depending upon the settings in your computer's BIOS/UEFI settings.  Sometimes the selection is plain, like:"legacy before UEFI", or "UEFI before legacy".  Sometimes less plain CSM mode (compatibility mode).  Usually you install the same way the other OSes are installed, but with an external disk, if your machine does the automatic mode switch (like Lenovo), it doesn't matter as much, as long as you just want to run the OS on the external disk (ie. if UEFI mode, don't try to boot the external disk's grub, then try to run legacy windows).

---

### Post by oldfred on 2017-03-12
Just be sure to install in same boot mode as Windows 7 and Ubuntu on internal drive.
And how you boot install media UEFI or BIOS is how it installs.

Best with external drives to partition in advance.
And you can use gpt whether booting in BIOS or UEFI mode. But if internal installs are BIOS, UEFI will not correctly install as you will not have gpt and an ESP - efi system partiiton on internal drive for grub.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
With gpt, you need either the ESP - EFI system partition (FAT32 with boot flag) or the bios_grub partition(unformatted with bios_grub flag). I actually put both as first two partitions on every larger device including 16GB flash drives. Then I can configure for either BIOS or UEFI boot without later having to try to re-arrange partitions if I want to change boot mode.

---

