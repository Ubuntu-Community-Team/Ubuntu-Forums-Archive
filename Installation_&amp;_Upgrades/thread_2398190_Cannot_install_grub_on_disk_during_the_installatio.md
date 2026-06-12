---
title: "Cannot install grub on disk during the installation"
date: 2018-08-08
forum: Installation &amp; Upgrades
---

### Post by guelo509 on 2018-08-08
Hello, 

I have an Intel Server, I have to install ubuntu in raid soft Mirroir.

I have 2x 3TB disks. 

I create a swap partition, a boot partition and a / partition

The system cannot install the grub at the end of the installation.

Do you have an idea?

Thanks

---

### Post by oldfred on 2018-08-08
UEFI or BIOS install?

If drives are over 2TiB, then you are using gpt partitioning.
And with gpt you have to have an ESP - efi system partition if UEFI boot or a bios_grub partition if BIOS boot, for grub to install correctly.
You you boot install media UEFI or BIOS is then how it installs.

I do not know servers, but now there are two Ubuntu server installers. I believe they updated the newer gui -  subiqity based one with 18.04.1 to now work with RAID.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Ubuntu_Server](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Ubuntu_Server)

---

