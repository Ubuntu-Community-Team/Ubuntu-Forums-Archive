---
title: "Grub error only load Ubuntu"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by xab on 2005-04-08
Hello i just installed Ubuntu worked really great untill y reboot my machine and started mi other OS (WinXP) the winxp started fine but when i tried tu access the cd the machine reboot by itself so i tried to load again winxp but grub gives me this message and freeze:

[SIZE=1]
root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1[/SIZE]

Thank you in advance for the help... Sory for my awfull english
By the way Ubuntu loads with no problem.

---

### Post by dataw0lf on 2005-04-08
Go into your BIOS settings and change the harddrive setting 'Auto' to 'LBA" (or it might be 'LARGE')

---

### Post by xab on 2005-04-08
[QUOTE=dataw0lf]Go into your BIOS settings and change the harddrive setting 'Auto' to 'LBA" (or it might be 'LARGE')[/QUOTE]

I did that now grub gives me an error 22 or 23 doesnt mather... dont now why but the 3rd partition (FAT32) is broken too y really dont now what the hell happen but the ntfs partition and and the fat32 was all messed up im reinstalling... thanks anyway

---

