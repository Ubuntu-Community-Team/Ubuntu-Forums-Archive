---
title: "Duel boot interrupt startup"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by Philip_Edwards on 2020-07-29
Hi,
Tomorrow, I've been volunteered to show some friends how to run Ubuntu from a USB flash drive.
Now, I'd like to demonstrate this on my Acer duel boot machine.....HOWEVER, I'd never noticed before but when you start a duel boot machine there doesn't appear to be an option whereby you can get the machine to boot from the USB drive.

Or is there?

Phil

---

### Post by oldfred on 2020-07-29
You should have entry in UEFI boot menu for flash drive.
Many UEFI need setting to allow USB boot or allow full USB support or both. Especially if UEFI Secure boot is on.
Some tools that create a USB flash drive installer, may make it BIOS boot only or UEFI boot only, even though ISO is configured to be either one. Make sure installer is in correct boot mode (UEFI) both configuration on flash drive and selection in UEFI boot menu.

If you updated UEFI from Acer, it may have reverted settings to defaults and you need to update again.

Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI

Eternal drives boot in UEFI boot mode from a FAT32 formatted partition with boot/esp flags. And the file used is /EFI/BOOT/bootx64.efi. That file is a copy of grub just for booting live installer.

---

### Post by Philip_Edwards on 2020-07-30
Thanks. Fixed

---

