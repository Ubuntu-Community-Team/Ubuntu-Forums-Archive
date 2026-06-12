---
title: "Trying to convert install on BIOS/MBR to EFI/GPT: can't load efivars kernel module"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by ferdez on 2014-09-10
Hi all,

I'm trying to convert a 14.04 MBR instalation to EFI but the kernel does not load the efivars module needed to run efibootmgr later (the disk is already GPT partitioned). It seems that this module is not even installed.

Anyone knows what package needs to be installed so that this module is loadable by the kernel?

TIA

Fernando

---

### Post by oldfred on 2014-09-10
If you have a BIOS install of Ubuntu on a gpt drive you should just need to uninstall grub-pc and install grub-efi or now grub-efi-amd64. Boot-Repair will do this for you.
You must have the efi partition preferable near beginning of drive for grub to correctly install.

Once booting in BIOS mode UEFI does not work and vice-versa. The two boot modes are not compatible and once you start booting in one mode you cannot switch to the other mode. 

The efibootmgr seems to only work when booted in UEFI mode, but you can boot Ubuntu live installer in UEFI mode to use it.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

[/URL] Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


While a flash drive, process is the same:
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by ferdez on 2014-09-11
> **oldfred said:**
> If you have a BIOS install of Ubuntu on a gpt drive you should just need to uninstall grub-pc and install grub-efi or now grub-efi-amd64. Boot-Repair will do this for you.
You must have the efi partition preferable near beginning of drive for grub to correctly install.

I already had installed grub-efi with synaptic but it didn't solve the issue. I tried a boot-install manually, and it installed grub on the EFI partition but when it got to the part of configuring the EFI firmware with efibootmgr it complained the kernel did not support EFI.

I'm now going to try use the Boot Repair disk.

Thanks.

Fernando

---

### Post by oldfred on 2014-09-11
Just be sure to boot Boot-Repair in UEFI mode. 
Or from live installer in live mode, you should then be able to run efibootmgr.

---

