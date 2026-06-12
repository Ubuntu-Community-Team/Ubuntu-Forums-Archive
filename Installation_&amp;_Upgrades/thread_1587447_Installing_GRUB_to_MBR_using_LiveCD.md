---
title: "Installing GRUB to MBR using LiveCD"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by aEx155 on 2010-10-03
I currently have a a hard drive with one partition for WinXP (C:\) and 12GB of free space that I want to install Ubuntu to.

Is there a way to install grub to the MBR so I can do the "InstallfromHardDrive" method of installation without having to use something like grub4dos by installing grub with a LiveCD?

On the C:\ partition I have a folder called "\boot" containing the linux and initrd.gz files already.

Just FYI, I'm install linux with the LiveCD I'm using because of optical drive errors, which is why I'm trying to do this an alternate way

---

### Post by Mark Phelps on 2010-10-03
You can certainly copy Linux files to MS Windows partitions, in this case, your "C" drive -- which is probably an NTFS partition.

But you can't run the install from inside MS Windows.

And you can't install Ubuntu to an NTFS filesystem.

I've heard there's a way to download the Wubi ISO and install using it -- but I personally stay away from Wubi because MS Windows presents enough problems without risking my Ubuntu install with it as well.

---

### Post by aEx155 on 2010-10-03
> **Mark Phelps said:**
> You can certainly copy Linux files to MS Windows partitions, in this case, your "C" drive -- which is probably an NTFS partition.

But you can't run the install from inside MS Windows.

And you can't install Ubuntu to an NTFS filesystem.

I'm trying to install grub so that I can use it to access the kernel files that reside on the C:\ drive to install linux into the unallocated space on my drive.

I've done it with grub4dos, but I don't really want to go that route.

I've done a bit of reading on network installs but that requires installing debootstrap; will that work with a LiveCD and not a floppy/USB drive?

EDIT: This is essentially what I'm trying to do, but it needs grub to be installed first: [https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)

---

### Post by oldfred on 2010-10-03
I installed grub to my FAT32 USB drive and it just installs to the MBR and creates /boot/grub with its files. I then added grub.cfg to loop mount the ISO directly without having to install the kernel. grub's /boot will interfere with /Boot in win7 or Vista but should work with XP. You must have XP if your current /boot does not interfere with windows.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

