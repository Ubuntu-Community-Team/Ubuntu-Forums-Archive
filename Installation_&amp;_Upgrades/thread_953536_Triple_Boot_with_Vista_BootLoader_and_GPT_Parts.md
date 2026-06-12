---
title: "Triple Boot with Vista BootLoader and GPT Parts?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by shaithis on 2008-10-20
I was wondering if it's possible to boot Ubunta (installed to a GPT partition) when the system boots the Vista bootloader off of an MBR partition?

So far I have tried using NeoGrub (EasyBCD can install this and the Vista bootloader can pass control to it) but GRUB errors like crazy and when I drop to the GRUB commandline and try to select the drive with linux on, I get told that it cannot read the partition.

I have tried installing GRUB to that partition alone (and adding the relevant info to the Menu.lst) but it errors on selection. I have tried the rootnoverify and the find --set-- options to select the boot drive, both fail.

Firstly, can any version of GRUB boot a GPT Ext3 partition from a RAID array, while GRUB itself is installed on an MBR drive?

Secondly, if so, which versions of GRUB? (NeoGRUB, WinGRUB, GRUB, GRUB2 ...) and can that version be installed as NeoGRUB is? (i.e. Vista bootloader can pass control to it)

Many TIA
:)

---

