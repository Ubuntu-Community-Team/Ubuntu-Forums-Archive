---
title: "grub and access to raid"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by dragoncamulos on 2008-05-05
OK, i need some help.   I'm trying to get a dual boot, Ubuntu/xp install with 8.04 on its own dedicated hard drive and windows installed on two drives setup as raid1. So far, the closest I've gotten to having this system finally setup was to set the dedicated drive as the primary drive in the BIOS.  then with Ubuntu installed and the grub loader on the dedicated drive, i can actually get to the grub menu.  at this point i can choose xp and boot right in but if I choose Ubuntu, i get an error 21 : Selected disk does not exist.  Now if i make a temporary change to grub entry and change the drive that grub is looking for Ubuntu to (hd0,0) from (hd0,2) Ubuntu boots fine.  I've tried modifying the grub settings with Grubed and changed that entry to make it permanent but after i do, i can no longer get windows to load.  it just sits there but Ubuntu boots just fine.   

Has anyone else had any luck getting a system like mine to work?

---

