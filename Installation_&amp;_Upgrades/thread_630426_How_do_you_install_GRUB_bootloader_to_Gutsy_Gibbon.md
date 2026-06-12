---
title: "How do you install GRUB bootloader to Gutsy Gibbon"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by straptin958 on 2007-12-03
The thing is that i got a dual hard drive system and I do want to have the bootloader so i can choose to go to Windows XP.. It jus takes away from the "UBUNTU EXPERIENCE" having to go through the BIOS to boot Windows XP

---

### Post by meierfra on 2007-12-04
Open a terminal (Applications->Accessories->Terminal) and post of the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```
(Both "l" are lowercase "L".)

---

