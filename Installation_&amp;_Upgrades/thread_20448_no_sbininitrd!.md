---
title: "no /sbin/initrd!"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by rudeboyskunk on 2005-03-16
i'm trying to install the 2.6.11.4 kernel, but i get to the part where i type in /sbin/mkinitrd /boot/initrd-2.6.11.4.img 2.6.11.4 and i find out there is no /sbin/initrd

would it be /sbin/Update-initrd???

or have i done something horribly, horribly wrong?

this is the first time i've ever compiled/installed a new kernel.  before i've always had someone else do it or just run with the distribution's default kernel/kernel settings.

---

### Post by void on 2005-03-17
try the following
mkinitrd -o /boot/initrd-2.6.11.4.img 2.6.11.4

---

