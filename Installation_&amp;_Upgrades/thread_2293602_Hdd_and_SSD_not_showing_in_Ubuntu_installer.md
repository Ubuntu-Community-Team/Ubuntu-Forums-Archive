---
title: "Hdd and SSD not showing in Ubuntu installer"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by ben174 on 2015-09-06
Hi, ive built a my first pc, and trying to install Ubuntu.

My bios shows both the ssd and the hdd but ubuntu cannot see these when trying to install.

I have tried using both IDE and AHCI settings in the bios, doesnt make a difference, currently set to AHCI.

sudo parted -l shows:

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot

sudo fdisk -l

Disk /dev/sda: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Gparted shows only the usb


This is obviously the USB i have the iso mounted on.

any help would be much appreciated.,

---

### Post by oldfred on 2015-09-06
AHCI is correct, not IDE which is for older drives.

Some UEFI/BIOS have additional settings to turn on or activate drives?

What motherboard?

If Asrock - do not use asmedia port for any device:
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by ben174 on 2015-09-06
I can't find any other setting to turn the drives on. 

It's an ASRock AM1B-ITX

I've had a look through all the links you have given and nothing seems to be of any real help thanks anyway.

---

### Post by oldfred on 2015-09-06
[http://arstechnica.com/civis/viewtopic.php?f=8&t=1252203](http://arstechnica.com/civis/viewtopic.php?f=8&t=1252203)

> It was a little quirky at first. It would hang or take a long pause  before getting to the bootloader  if there were devices connected to the  secondary SATA ports (provided by an ASMedia chip), but I figured out  that disabling "Compatibility Support Mode" in the UFEI setup screen  actually solved the problem. 

---

### Post by ben174 on 2015-09-06
Thanks altered the CSM but no difference, still doesn't see them. 

Im at a loss at the moment, can't seem to figure it out!

This was my first build, is it possible I've done something wrong at the build stage? Something I've missed?

---

### Post by oldfred on 2015-09-06
If UEFI/BIOS see drives then they should be connected ok.

But use of the ASMedia ports has caused major issues with Asrock motherboards.
Are you using standard ports just 1 & 2, not a1 & a2? 
Manual shows the standard ports on right.

---

### Post by ben174 on 2015-09-07
Yes they are connected to port 1 and 2, no a1 or a2.

---

