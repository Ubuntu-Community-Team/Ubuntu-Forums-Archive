---
title: "grub boot loader failed to install"
date: 2016-11-16
forum: Installation &amp; Upgrades
---

### Post by zzxxcc2056 on 2016-11-16
Hi i tried to install ubuntu 16.10 and am getting the message " the 'grub-efi-amd64-signed' package failed to install.

[http://paste2.org/nzavXZ3G](http://paste2.org/nzavXZ3G)

What i need to do ?

Thanks

---

### Post by Dennis N on 2016-11-16
Your disk sda has an msdos partition table, so Windows is installed in bios mode. You are trying to install Ubuntu in uefi mode which won't work here - you have to have the same installation type (bios) as Windows.

To do that the installer has to be booted in bios mode.

---

### Post by oldfred on 2016-11-16
It looks like even though you booted Boot-Repair in UEFI mode, that is is offering to reinstall the BIOS boot version of grub or grub-pc.

Since you have a new UEFI system, but have Windows in the 35 year old BIOS/MBR configuration, you need to always boot in BIOS mode.

---

