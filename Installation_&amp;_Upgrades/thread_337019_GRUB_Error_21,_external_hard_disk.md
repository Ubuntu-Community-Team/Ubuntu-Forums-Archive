---
title: "GRUB Error 21, external hard disk"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2007-01-12
To an Acer notebook computer I plugged in a external hard disk via USB.

Unfortunately I hit continue when the question appeared, where to put Grub. Default was hd0.

Now the system boots till:

Grub Loading stage 1.5

grub loading, please wait
Error 21


I tried all kind of things, like boot from live cd, terminal windows and grub, 
grub> root (hd & tab offers me hd0 and hd1, I choose hd0) and complete the line to:
grub> root (hd0,1)
grub> setup (hd0)

Error .. not found

grub> find /boot/grub/stage1

ends also with not found.

How can I recover the MBR (I believe that one got in trouble)


bye

Ronald Wiplinger

---

### Post by logos34 on 2007-01-12
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

---

