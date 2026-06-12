---
title: "ubuntu 16.04 : grub-efi-amd64-signed failed"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by sam-bits on 2016-04-27
[http://paste2.org/Kxtp77LO](http://paste2.org/Kxtp77LO)

My first installation was ubuntu 14.04 which booted in UEFI mode. Next dual installation was fedora, which was installed in legacy BIOS mode most likely because I installed using DVD drive in non UEFI mode.
Now the new installation ( started in EFI mode of DVD )  fails in the end saying 

     grub-efi-amd64-signed failed to install into /target/.      Without GRUB boot loader, the installed system will not boot

Have looked around fiddling with things. But nothing seems to work.

---

### Post by Dennis N on 2016-04-27
Your disk has a MS-DOS partition table. For UEFI installation, you need a GPT partition table with an FAT32 EFI system partition. The EFI system partition is where grub has to install, but it cannot since there isn't one. That is why you get the failure message.

If you instead install the new OS in BIOS mode, it should succeed. Boot the installer in BIOS mode instead of UEFI mode.

---

