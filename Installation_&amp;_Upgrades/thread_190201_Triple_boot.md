---
title: "Triple boot?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by mechel on 2006-06-06
I have a computer that is dualbooting windows XP, and ubuntu 6.06. I was wondering if there is an easy way to triple boot with win98 without having to uninstall xp or ubuntu.

---

### Post by kornelix on 2006-06-06
[QUOTE=mechel]I have a computer that is dualbooting windows XP, and ubuntu 6.06. I was wondering if there is an easy way to triple boot with win98 without having to uninstall xp or ubuntu.[/QUOTE]

You can try to edit the file /boot/grub/menu.lst and add a boot for Win 98.
(I assume it would look like the following one for Win XP). 

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

You need to change the (hd0,0) entry to reflect the partition number for Win 98: (hd0,0) ... (hd0,9). If not sure, put several variations in the file so you can try all of them.

---

