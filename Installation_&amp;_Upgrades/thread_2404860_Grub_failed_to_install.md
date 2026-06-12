---
title: "Grub failed to install"
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by omerdav on 2018-10-29
Hi, I've had an issue while trying to install Ubuntu 18.04 on my usb flash drive (I'm trying to have it installed on my usb and boot it, I don't want a live usb). The installation went well except for getting an error at the end of it, saying that grub could not be installed. 
Any help would be appreciated, I've tried to install it from a VM if that indicates anything, Thanks!

---

### Post by oldfred on 2018-10-29
Did you partition in advance?
Using UEFI or BIOS install?

Your partitioning MBR (BIOS) or gpt (BIOS or UEFI) has to match install boot mode. And if gpt you have to have either bios_grub partition for BIOS boot or an ESP - efi system partition for UEFI boot.
UEFI only boots from ESP on external drive and /EFI/Boot/bootx64.efi. But grub normally creates /EFI/ubuntu in first drive's ESP, usually internal drive. Not sure with VM?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

