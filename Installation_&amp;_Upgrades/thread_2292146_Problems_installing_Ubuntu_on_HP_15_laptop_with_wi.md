---
title: "Problems installing Ubuntu on HP 15 laptop with windows 10"
date: 2015-08-25
forum: Installation &amp; Upgrades
---

### Post by Paul Barnett on 2015-08-25
I am trying to install Ubuntu 15. on a laptop HP 15 as a dual boot. I have adjusted bios to legacy with the dvd\cd drive as first level. I turned off fast-load. The computer will not boot from this drive. I have also attempted booting from a USB drive with no success. Am I missing something?

---

### Post by grahammechanical on 2015-08-25
Was Windows 10 installed in EFI mode? If it was then Ubuntu will have to be installed in EFI mode as well. Otherwise, when you get Ubuntu installed you will not be able to load Windows 10.

---

### Post by Paul Barnett on 2015-08-25
> **grahammechanical said:**
> Was Windows 10 installed in EFI mode? If it was then Ubuntu will have to be installed in EFI mode as well. Otherwise, when you get Ubuntu installed you will not be able to load Windows 10.

This is a new computer so windows 8 was pre-installed and upgraded to windows 10.I am not sure which mode was used.

---

### Post by ubfan1 on 2015-08-25
UEFI mode, since that's what preinstalled Win8 was in.  Did you try turning off secure boot (not UEFI mode, just the secure boot)?  Some machines won't boot USB with secure boot on.  Eventually, after the HD install, you will need to change the bootloader label to "Windows Bootloader" and maybe the filename too (like boot-repair does), but that problem should not affect the USB.

---

### Post by Paul Barnett on 2015-08-25
Secure boot is disabled. I still cannot boot from either USB or DVD.

---

