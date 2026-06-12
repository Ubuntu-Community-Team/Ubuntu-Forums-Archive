---
title: "Dual boot UEFI Windows 10 - Upgrade Ubuntu 14.04 - efibootmgr"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by kracheck on 2016-02-15
Hi there,

Currently I am dual booting Windows 10 with Ubuntu 14.04. When the new LTS comes out I'll go for a clean install but again dual boot. 

I was wondering, will the clean install automatically remove the old Ubuntu entry from the efibootmgr or will I end up with 2 entries. If I do end up with two entries how will I be able to tell which one is the new one in order to be able to remove the old one ?

---

### Post by Dennis N on 2016-02-15
In my experience, the Ubuntu just installed is placed first in the EFI boot manager's boot order list. It will boot by default. If you have another Ubuntu version still installed as well, it will disappear from the choices in the EFI boot manager, but can then be booted from the grub menu of the other.

You should not have an entry remaining for an OS that no longer exists on the disk.

---

### Post by kracheck on 2016-02-15
ok thanks for the info.

---

