---
title: "Trouble in using UEFI to install ubuntu 10.10"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by gongwayne on 2011-03-20
Hi,
I'm a newer about ubuntu.
Today I'd like install ubuntu on my desktop. The motherboard is intel DP55WB, according to intel, it supports UEFI. So i made a USB stick to install Ubuntu.
However, i found the ubuntu is BIOS booted after the installation.
 
Could someone  help me? Looking forward someone experienced in succeeding in installation using UEFI.
 
Thanks a lot

---

### Post by srs5694 on 2011-03-21
AFAIK, most modern Intel boards have an EFI boot *option*, but they don't boot in EFI mode by default. Unless you've got a very specific reason to want to use EFI mode, it might be best to just stick with BIOS mode.

If you do want to use EFI mode, you can convert it; but you'll need to replace the grub-pc package with grub-efi and re-install GRUB. This will involve writing some GRUB files to the EFI System Partition on the boot disk. (If the disk lacks an EFI System Partition, you'll need to create one.) Note that this is very "bleeding-edge" stuff.

---

### Post by fr_ank on 2011-06-23
Hi,

you have to enable the UEFI boot in "BIOS" and to boot the installer in UEFI mode. For example I can choose the boot order by pressing F10. 
If the UEFI stuff is enabled I can see the DVD drive twice with and without UEFI. That's the reason why the UEFI installation from USB stick doesn't work for me.

---

