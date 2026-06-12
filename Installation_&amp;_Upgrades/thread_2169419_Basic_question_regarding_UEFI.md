---
title: "Basic question regarding UEFI"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by geohei on 2013-08-22
I did quite some fiddling around UEFI and efibootmgr, but one of the things I missed is the "link" between the bootmanager (grubx64.efi) and the partition the system resides.

Example (yes, I know ... 2 ESPs - for testing!):

```
...
Command (? for help): p
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7B0E6510-D248-42E6-BB41-8F1545A740AA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 38072941 sectors (18.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI System - Windows
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       210184191   100.0 GiB   0700  Basic data partition
   4       210184192       315041791   50.0 GiB    0700  Basic data partition
   5       315041792       315246591   100.0 MiB   EF00  EFI System - Ubuntu
   6       315246592       420104191   50.0 GiB    0700  Ubuntu
   7       420104192       462047231   20.0 GiB    8200  Linux swap
```

To make an entry into UEFI boot manager, I use:

```
efibootmgr -c -d /dev/sda -p 5 -l "\EFI\ubuntu\grubx64.efi" -L "Ubuntu"
```

How does grubx64.efi (located in sda5) know that it should continue to boot in sda6 (which resides the Linux on an ext4 filesystem)?

---

### Post by oldfred on 2013-08-22
You can only have one efi partition per drive. Not sure what happens with two?

I do not know details of efibootmgr, but I would think you still have to install grub from Ubuntu. The boot manager is just adding a boot entry into the UEFI memory.

       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by ubfan1 on 2013-08-22
grubx64.efi uses grub.cfg just like the old grub to select which system to boot.  The location /EFI/ubuntu/grub.cfg is different, but newer releases just have a three line stub for grub.cfg which brings in the "maintained" grub.cfg from /boot/grub/grub.cfg

---

### Post by geohei on 2013-08-23
> **oldfred said:**
> You can only have one efi partition per drive. Not sure what happens with two?
2 EFI partitions are allowed by UEFI specifications.
See article 2 (from srs5694)
[https://bbs.archlinux.org/viewtopic.php?id=168503](https://bbs.archlinux.org/viewtopic.php?id=168503)
> **oldfred said:**
> I do not know details of efibootmgr, but I would think you still have to install grub from Ubuntu. The boot manager is just adding a boot entry into the UEFI memory.
Yes, sure. This is not about grub. UEFI starts grubx64.efi (= bootloader), and then grub takes over.
> **oldfred said:**
> Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
All this is more or less known, but doesn't answer my question.
How does grubx64.efi (located in sda5) know that it should continue to boot in sda6 (which resides the Linux on an ext4 filesystem)?
> **ubfan1 said:**
> grubx64.efi uses grub.cfg just like the old grub to select which system to boot.  The location /EFI/ubuntu/grub.cfg is different, but newer releases just have a three line stub for grub.cfg which brings in the "maintained" grub.cfg from /boot/grub/grub.cfg
grubx64.efi is located in ESP.
grub.cfg is located in Ubuntu partition (/).
/EFI/ubuntu/grub.cfg doesn't exist on my system.
/boot/grub/grub.cfg exists on Ubuntu partition (/) and is required, but how does grubx64.efi know where to find this file since it has no knowledge about the lacation of the Ubuntu partition (/).

---

### Post by oldfred on 2013-08-23
thread closed. You started a new thread on similar related issues.

[http://ubuntuforums.org/showthread.php?t=2169804](http://ubuntuforums.org/showthread.php?t=2169804)

---

