---
title: "Vista disapeared in bootloader"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by BlackLLama on 2008-07-14
yes hello, i attemped to dual boot ubuntu with vista, i had vista installed first i did everything right, i did disk partition correctly. i correctly installed Ubuntu and i even have the xx gb media file, with all my vista files. but vista fails to show up in the bootloader only ubuntu shows up? what is the fix to this?

---

### Post by logos34 on 2008-07-14
try adding an entry to bottom of menu.lst like the example provided.

gksudo gedit /boot/grub/menu.lst

> title        Windows Vista
root        (hd0,0)
makeactive
chainloader    +1

this is assuming vista is the first partition.  If there's a recovery/utility partition instead and vista is second, try 'root (hd0,1)'

If unsure, post your 

**sudo fdisk -l**

---

### Post by BlackLLama on 2008-07-14
hey man thanks, its works now, problem solved

---

