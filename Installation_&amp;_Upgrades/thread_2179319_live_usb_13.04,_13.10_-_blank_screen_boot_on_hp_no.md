---
title: "live usb 13.04, 13.10 - blank screen boot on hp notebook w/ Radeon HD 7520G"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by patrick0 on 2013-10-07
I've read a zillion posts about blank/black screen booting problem but haven't found a solution -
New hp pavilion g6 notebook with Trinity Radeon HD 7520G graphics controller. Windows 8 pre-installed, uses UEFI booting. I have "secure boot" turned off, windows still boots.
Trying to boot ubuntu either 13.04 or 13.10 64-bit "live" from a usb flash drive (problem is the same with either version): The kernel will boot, but (from dmesg) lightdm exits with an error code so blank screen. Right before the lightdm failure, there is the following message: "pci 0000:00:01.0: Invalid ROM contents". Doing an lspci, it turns out that 00:01 is in fact the display controller.

Does this just mean that the kernel doesn't work with this display controller? Or any possible workaround?

---

### Post by oldfred on 2013-10-07
A lot of the new system need these settings instead of nomodeset.
 acpi_osi=Linux acpi_backlight=vendor

Someone else also had issues with lightdm and changed to gdm.
      
 Some laptops with black screen find switching from lightdm to gdm works  - user did not post all the details.
Or with lightdm add sleep 1 in 
/etc/init/lightdm.conf

---

