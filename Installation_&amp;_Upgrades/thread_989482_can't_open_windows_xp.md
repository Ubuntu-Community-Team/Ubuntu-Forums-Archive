---
title: "can't open windows xp"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by ryan! on 2008-11-21
can't open windows xp.....it goes straight to ubuntu................please help

---

### Post by caljohnsmith on 2008-11-21
How about when you boot into Ubuntu, open a terminal (Applications > Accessories > Terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And if the "hiddenmenu" line does not have a pound sign # in front of it, put one there:
```
# hiddenmenu
```
That way you should see the Grub menu on start up at least. If you need to add an entry to boot Windows in your Grub menu, then please also post:
```
sudo fdisk -l
```
And we can work from there if you want.

---

