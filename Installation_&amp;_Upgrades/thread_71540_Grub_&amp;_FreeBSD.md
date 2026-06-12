---
title: "Grub &amp; FreeBSD"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by DJ Ubuntu on 2005-10-03
How to edit grub (menu.lst) to add the line FreeBSD 6?
I want to start boot it detects:
- XP
- Ubuntu 5.10
- FreeBSD 6

Can somebody help me?.

---

### Post by ow50 on 2005-10-03
This is what I used
```
title       FreeBSD 6.0
root        (hd1,1,a)
kernel      /boot/loader
savedefault
boot
```
If I remember correctly (hd1,1,a) means second hard disk, second partition, slice a, but I'm not sure on that.

---

### Post by DJ Ubuntu on 2005-10-03
Thanxs for your help!!:D

---

