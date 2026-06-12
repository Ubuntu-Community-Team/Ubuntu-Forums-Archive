---
title: "Grub2 Boot USB"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by William_Jonah_Roberts_ on 2014-01-10
After installing Ubuntu 13.10, my uefi boot priority is locked and when I try to move usb devices to the top and save, I get an access denied error.  My question is; is it possible to add a grub2 entry to boot from usb devices (ie live usb keys or bootable hard drives?) Without having to identify them and the vmlinuz file?  (Similar to how bios would boot a bootable flagged drive...)

---

### Post by sudodus on 2014-01-12
I'm not very experienced with UEFI, I've just started to learn about it (with one new laptop), but I suggest that you try to add a grub2 entry. See this link about chainloading, that might work if you chainload to a USB device which can boot in UEFI mode (for example a current Ubuntu 64-bit version (12.04.3 or 13.10)).

[https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

---

