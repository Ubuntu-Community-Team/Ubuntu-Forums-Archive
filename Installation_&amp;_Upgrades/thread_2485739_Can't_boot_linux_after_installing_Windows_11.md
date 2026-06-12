---
title: "Can't boot linux after installing Windows 11"
date: 2023-04-07
forum: Installation &amp; Upgrades
---

### Post by amannan-123 on 2023-04-07
Here's the report: [https://paste.ubuntu.com/p/RrzWT7YwBB/](https://paste.ubuntu.com/p/RrzWT7YwBB/)
GRUB is somehow deleted and I can't install it again

---

### Post by oldfred on 2023-04-07
Did you delete & create new ESP - efi system partition, your sdb3? Line 238 is mount of ESP, but that partition does not exist.
You probably need to update that fstab entry with new UUID before running fix from Boot-Repair.

You show no UEFI entry for Ubuntu in UEFI, see line 102. 

You can use Boot-Repair's advanced mode, when booted in UEFI mode, and choose install & sdb to install UEFI version of grub.

---

