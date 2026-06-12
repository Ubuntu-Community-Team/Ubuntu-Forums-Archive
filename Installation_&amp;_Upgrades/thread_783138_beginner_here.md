---
title: "beginner here"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by mucmicu on 2008-05-05
Hi to all

I;m new to Ubuntu and i wish to install it with XP also.

which is the best approach for installation order?

windows first or ubuntu first?

---

### Post by game_plan on 2008-05-05
Depends on which boot loader you want to use.

I would personally install Windows first, partition the drive leaving room for Ubuntu. Then once windows is in install Ubuntu.

Reason being Ubuntu will automatically give you the option of which one you want at boot, windows you have to add Linux manually.

---

### Post by haiji on 2008-05-05
IMO is better to install XP first. Ubuntu installer is more clear and easy, and also have a partioning tool that lets you to prepare you hard disk for a multi-os system. But the most important point is that Windows installation will overwrite your MBR and remove GRUB (the multi-boot menu), you can fix this later but it's not as straight-foward as installing Ubuntu after Windows.

---

### Post by ilrudie on 2008-05-05
I agree.  Linux plays much nicer with existing windows installs than windows does with existing Linux installs.  Installing windows first is the easiest way to go.

---

