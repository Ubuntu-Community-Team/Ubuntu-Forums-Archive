---
title: "Installation of Ubuntu for a UEFI boot from USB"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by morbuscordis on 2017-07-16
I need a USB stick with a portable 64-bit version of Ubuntu on. I've done it with legacy, but that's only 32-bit. I need the bootloader and OS on one USB stick, so that I can take it anywhere, and boot from any computer that supports UEFI. Please note that I would use the boot menu from the BIOS in order to do this, I already have Windows on my PC. I do not have any form of Linux. I do have the Ubuntu installation media on a USB drive (No disk tray in on my laptop), so I can live boot.
Thanks.

---

### Post by C.S.Cameron on 2017-07-16
[B]mkusb
[/B]
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by johndough2 on 2017-07-16
Hi

Try

LinuxLive USB Creator  or  MultiBootUsb

these have the capacity to install a choice of many flavours of linux and run readily under windows.

---

### Post by sudodus on 2017-07-16
In Windows you can clone an operating system with [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager). You can 

- start from an iso file and create a live-only USB drive with Ubuntu or an Ubuntu 64-bit family operating system, that works in both UEFI and BIOS mode. The corresponding iso files have the string **amd64** in the file name.

- start from an image file and clone the original system in the image to a USB drive. This system can be anything, for example an installed system or a persistent live system with some special tweaks, for example mkusb installed. You can find (and download) such systems via the following link, [Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

---

