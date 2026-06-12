---
title: "USB Stick boot issues with UEFI or BIOS"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by mellon85 on 2015-03-18
I have tried installing Ubuntu 14.04.2 and 14.10

Gygabyte motherboard
12GB Ram
Radeon R9 270x
D-Link 556

The system just doesn't book.. if I try in legacy mode I get a black screen with this repeating..

gfxboot.c32: Not a COM32R image
boot:


and in UEFI mode I can only stare at the pinks loading screen with some occasional hard drive access.
Between tries I also trie with another distribution (Fedora 21) and that works immidiately instead :s

---

### Post by sudodus on 2015-03-18
> gfxboot.c32: Not a COM32R image

indicates a known bug with Unetbootin and the Ubuntu Startup Disk Creator (and maybe some other similar tools). Please use [mkusb]("https://help.ubuntu.com/community/mkusb") in linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows in order to install/copy/flash the iso file into the pendrive.

---

### Post by plucky on 2015-03-18
> gfxboot.c32: Not a COM32R image
boot:

Also type **help** at the prompt will give you options to continue the boot.

Good Luck

---

### Post by mellon85 on 2015-03-18
> **sudodus said:**
> indicates a known bug with Unetbootin and the Ubuntu Startup Disk Creator (and maybe some other similar tools). Please use [mkusb]("https://help.ubuntu.com/community/mkusb") in linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows in order to install/copy/flash the iso file into the pendrive.

I tried with both softwares to generate the USB key.. but nothing works.

In the end I resorted to burn a DVD and try to boot from it, and it booted, but unfortunately nothing from USB works.
I get the error
usb 1-1: device descriptor read/64, error -32

repeated a lot in dmesg, and no mouse or anything working... and in fact I noticed that even fedora can't access my xbox controller (but can access my mouse)... but ubuntu instead just doesn't access any USB device.. while windows works fine :s

---

### Post by sudodus on 2015-03-18
You might need some [boot options]("https://help.ubuntu.com/community/BootOptions"), for example **nomodeset**, and then install a proprietary driver for the radeon card.

You can also try to boot after unplugging all USB devices.

---

### Post by oldfred on 2015-03-18
You mentioned Gigabyte Motherboard. 
They all seem to have IOMMU settings that must be changed from default and/or need boot parameter for IOMMU.

        GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)

Others with different models all Gigabyte have reported the IOMMU issue.

---

### Post by mellon85 on 2015-03-19
I'll try playing around with the IOMMU today, thanks for the help! Probably it was just that.. something I would have never thought about

---

### Post by mellon85 on 2015-03-20
I won't probably buy another Gigabyte :D (I have a 990FXA UD3 rev4.0 without the beta bios installed)
the first post solved the issue of mine, even though I can leave the IOMMU enabled and everything works, but as read from the post it may explain why Windows was freezing sometimes and now it stopped

> **oldfred said:**
> You mentioned Gigabyte Motherboard. 
They all seem to have IOMMU settings that must be changed from default and/or need boot parameter for IOMMU.

        GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)

Others with different models all Gigabyte have reported the IOMMU issue.

---

