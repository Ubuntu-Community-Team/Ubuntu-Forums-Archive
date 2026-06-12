---
title: "Installation error: The partition table format in use on your disks normally requires"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by svmpuabuster on 2015-04-18
Error :-

**The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as “Reserved BIOS boot area” and should be at least 1 MB in size. Note that this is not the same as a partition mounted on /boot. If you do not go back to the partitioning menu and correct this error, bootloader installation may fail later, although it may still be possible to install the boot loader to a partition.**


I am trying to dualboot it alongside Windows 8.1. I get this error after I configure the "root", "home" and "swap" partitions.

Any help?

---

### Post by oldfred on 2015-04-18
If Windows 8 is pre-installed it is booting in UEFI mode and requires gpt partitioning.
But the error you are getting is because you are installing BIOS boot mode on a gpt partitioned drive. If you really want BIOS boot for Ubuntu then you need a tiny 1 or 2MB unformatted partition with the bios_grub flag in gparted. If you use gdisk to create partition it is code ef02. It actually is a very long GUID that is assigned with these short flags or codes.

But you probably do not want Ubuntu in BIOS boot and Windows in UEFI boot. You may have to go into UEFI boot menu and turn on/off UEFI or CSM/BIOS each time you reboot into the other system. 

Much better to install Ubuntu in UEFI boot mode.

How you boot install media is how it installs. Your UEFI boot menu for the Ubuntu installer with have two entries. One will say UEFI and name of flash drive and the other just the name of flash drive which then is BIOS boot.

Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
Installing Ubuntu on a Pre-Installed Windows 8 (64-bit) System (UEFI Supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

