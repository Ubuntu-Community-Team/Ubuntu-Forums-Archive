---
title: "windows xp hibernation problems on hardy"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by m_ch on 2008-05-13
hi everyone:
I have dual boot on mi laptop, windows xp on /dev/sda1 an ubuntu Hardy on /dev/sda6. Problem is when I try to start up windows, I select windows partition from menu grub, but nothing happens, the screen just turn black and ubuntu is unable to (automagiclly) mount the partition. I type the command "*sudo mount -t ntfs /dev/sda1 /windows*" but it returns me an error.

/boot/grub/menu.list appears to be fine:

[I]title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/I]

**I guess the problem was during the upgrade from gutsy to hardy (online) that the windows partition was on hibernation state!!**

Any ideas???
thanks in advance.

---

