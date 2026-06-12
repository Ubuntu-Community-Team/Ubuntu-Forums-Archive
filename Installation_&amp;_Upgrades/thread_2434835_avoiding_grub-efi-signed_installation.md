---
title: "avoiding grub-efi-signed installation"
date: 2020-01-11
forum: Installation &amp; Upgrades
---

### Post by lvm on 2020-01-11
Some time ago I installed 18.04 on UEFI motherboard using GUI installer. I was somewhat surprised by the fact that even though the secure (signed) boot was turned off in UEFI settings the boot disk was partitioned for EFI and the signed grub (grub-efi-amd64-signed) was installed, but it was doing its job and I let it go. The dire consequences are descried here: [https://ubuntuforums.org/showthread.php?t=2432759](https://ubuntuforums.org/showthread.php?t=2432759) and in many other posts in this forum. As far as I can remember the installed did NOT prompt for signed/unsigned grub selection - am I correct? Is it possible to install ubuntu with plain (unsigned) grub and no EFI partition on UEFI motherboard with secure boot turned off using the standard installer?

---

### Post by oldfred on 2020-01-11
Do not know if server installer with LVM does something different?

UEFI install will require an ESP - efi system partition as that is where UEFI boot files are.

Generally Ubuntu installs in the boot mode of flash drive/DVD installer. So if booted in UEFI Secure Boot mode, it will install in Secure Boot mode.
And selection of flash drive installer, is separate from UEFI settings. 
But most only boot flash drive in UEFI with Secure boot off or CSM (BIOS) mode if system setting has UEFI Secure Boot off.
Or only installs in Secure Boot mode if Secure Boot is on and allow USB boot is on. Having USB boot, is not normally considered secure as then someone else can boot system.

I have UEFI Secure Boot off and just installed 20.04 to test with 18.04 as main working install and it installed generic kernel.

---

