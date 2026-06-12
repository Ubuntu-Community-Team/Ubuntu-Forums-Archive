---
title: "No bootmgfw.efi.bak"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by dscul on 2013-02-26
I installed Ubuntu alongside windows but it still booted into the windows loader. Then I created an ESP partition and marked it as boot through GPARTED and ran boot repair which got me into Ubuntu.. which was nice..

The records created for windows gave the invalid efi file error so added records to custom_40 but trying these either (a) do nothing for a second and returns to grub or (b) the bootmgfw.efi file is the grub menu after boot repair? 

Please find the full information here
[http://paste.ubuntu.com/5569430/](http://paste.ubuntu.com/5569430/)

There are no backups of bootmgfw.efi or bootx64.efi just a .grb file for each and all files are the same size. Is there a way of creating a correct bootmgfw.efi (what is mentioned as bootmgfw.efi.bak in other threads) instead of what I think is just a copy of /boot/efi/EFI/ubuntu/grub64.efi? I would prefer not to look into restoring the machine to it original state (if possible) and trying to install Ubuntu again correctly.

---

### Post by oldfred on 2013-02-27
Welcome to the forums.

Your Windows install is in BIOS/MBR mode. You should just have boot flag on sda1 and do not need an efi partition unless Windows is installed in UEFI mode with gpt partitioning. It is a huge change to convert to gpt partitioning and convert Windows to UEFI mode to boot. Better to reinstall totally if you really want to use UEFI. 

But since your install is in BIOS mode, I would just leave it. Then you do not even need efi partition.

---

