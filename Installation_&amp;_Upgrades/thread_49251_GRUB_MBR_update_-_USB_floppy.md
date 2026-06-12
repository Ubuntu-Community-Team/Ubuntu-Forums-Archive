---
title: "GRUB MBR update - USB floppy"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by jomk on 2005-07-15
I have a computer that only has a USB floppy drive - I have not been able to make a floppy bootable. 

I am multi-booting various distros (kubuntu promises to become my favorite) and have a menu.lst that I have tweaked and would like to replace the current one on the MBR. How would this be done?

THX,
jomk

---

### Post by al7kz on 2005-07-16
Hi jomk,

run command

sudo  grub

grub> find /boot/grub/stage1

this lists all linux boot partitions, say the one with the tweaked menu.lst is (hd0,8):

grub> root (hd0,8)
grub> setup (hd0)
grub> quit

reboot

---

### Post by al7kz on 2005-07-16
sorry, now idea how the smily faces got in there. Say the partition with menu.lst is (hd0,3)

grub> root (hd0,3)
grub> setup (hd0)
grub> quit

---

