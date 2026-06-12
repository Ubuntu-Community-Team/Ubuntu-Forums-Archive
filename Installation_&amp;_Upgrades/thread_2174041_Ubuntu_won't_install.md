---
title: "Ubuntu won't install"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by nathan8 on 2013-09-12
I have dban'd my hd, I have tried both ubuntu 13.04 and 12.04 both 64 bits to install and though the live cd recognizes these previous installations when I try to install over it, when I boot from hd, heres the message:

PXE-E61: media test failure, check cable
PXE-M0F exiting broadcom pxe rom
no bootable device -- insert boot disk and press any key

hd is brand new. 
Plz help.

---

### Post by rencemc on 2013-09-12
Have you check the boot devices and order in the BIOS ?

---

### Post by nathan8 on 2013-09-12
> **rencemc said:**
> Have you check the boot devices and order in the BIOS ?

yes and I have tried taking the live cd out thus forcing the computer to boot from hd.
my computer is a travelmate p253-e and my processor is intel b960

---

### Post by rencemc on 2013-09-12
Is the "boot from LAN" option enabled in the BIOS boot menu ? If so, disable it.

---

### Post by sudodus on 2013-09-13
If your computer came with Windows 8, you have UEFI, and need to switch it off to boot the normal way with a BIOS system and an MSDOS partition table. If you cannot switch it off, you need a GPT partition table with a small UEFI (or EFI) partition. See this link

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

