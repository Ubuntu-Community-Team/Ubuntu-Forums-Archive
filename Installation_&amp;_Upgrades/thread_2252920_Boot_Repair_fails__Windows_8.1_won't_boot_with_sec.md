---
title: "Boot Repair fails / Windows 8.1 won't boot with secure boot enabled"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by m.reinecke on 2014-11-15
Hi,

I can boot into ubuntu with secure boot enabled as well as disabled. But I can only boot into Windows 8.1 when secure boot is disabled.

My setup:

SSD1:
- Ext4 Partition: "/" (Root)

SSD2:
- System restore partition
- EFI System Partition
- NTFS Partition: Windows 8

HDD:
- NTFS Partition: Data
- Ext4 Partition: /home
- Swap Partition

But I think this will be somewhere in my Boot-Repair log, too :)

[http://paste.ubuntu.com/9033194/](http://paste.ubuntu.com/9033194/)

Thanks for your help!

---

### Post by oldfred on 2014-11-15
I would think from UEFI you should be able to boot Windows with secure boot on as that is a Windows requirement.

But grub may not let you boot Windows. Not sure if this bug has been fixed or not.
 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi

---

### Post by m.reinecke on 2014-11-16
Mhh yeah, seems to be the same problem as the people there are facing. Thanks for bringing this up.

---

