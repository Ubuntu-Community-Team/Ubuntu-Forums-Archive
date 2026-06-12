---
title: "EFI Shell Loop. The eMMC has Ubuntu but I can not access it"
date: 2021-03-22
forum: Installation &amp; Upgrades
---

### Post by blaahgaming on 2021-03-22
Hi folks, I'm new to Ubuntu. I thank you in advance.

Have a MEDION laptop with x64Bit hardware but conversion or this is a device that is part of the fact that the device behaves like an x86Bit. Am with the Ubuntu 20.04 LTS installation to the point that the "bootia32.efi" file is able to get the BootRepair charges ([http://paste.ubuntu.com/p/RVhh6Td8dx/](http://paste.ubuntu.com/p/RVhh6Td8dx/)) on UEFI -Firmware must boot to the Ubuntu entry (mmcblk0p1 / EFI / ubuntu / shimx64.efi).

Now I have no idea how to continue, because I'm always in the shell, I also noticed that I have 3 boot options and have heard that EFI Shell is the last one. The first two are both Ubuntu but both come back into the shell ... 1. belongs to shimx64.efi 2. leads to grubx64.efi. My opinion is, I should flash the BIOS ..?

Many thanks again.

---

### Post by yancek on 2021-03-22
> Have a MEDION laptop with x64Bit hardware but conversion or this is a  device that is part of the fact that the device behaves like an x86Bit. 

I have no idea what you are trying to say here.  You have 64bit capable hardware and are installing a 64bit OS (Ubuntu).  You have an EFI install of Ubuntu with the proper files appering in the proper locations.  It appears that when you try to boot you loop back to the boot menu?  What is your reference to "bootia32.efi" ?  Line 35 in boot repair shows your boot order which has the ubuntu shimx64.efi file as first boot.  Is it when you select this option that you get the loop?

---

### Post by CelticWarrior on 2021-03-22
The reference to "bootia32.efi" suggests the hardware is one of those Bay Trail / Cherry Trail series with a 32-bit UEFI.
The Linuxium respin should give better results than the standard Ubuntu distributed ISO.

---

