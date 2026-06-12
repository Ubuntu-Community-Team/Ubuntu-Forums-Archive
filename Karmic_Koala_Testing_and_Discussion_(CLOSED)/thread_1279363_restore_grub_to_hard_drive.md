---
title: "restore grub to hard drive?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-09-30
I was playing around with windows and need to restore grub.
what command do i run from the live cd?
I only have one hard drive

---

### Post by testcees on 2009-09-30
Grub2?
if sda5 is your Ubuntu partiotion:
sudo mount /dev/sda5 /mnt
sudo grub-install /dev/sda --root-directory=/mnt

---

### Post by kansasnoob on 2009-09-30
I found this very helpful:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by ranch hand on 2009-09-30
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by sdowney717 on 2009-10-01
thanks it is grub2
> sudo mount /dev/sda5 /mnt
sudo grub-install /dev/sda --root-directory=/mnt 

worked fine. Yes it is sda5

to see it use sudo fdisk -l

---

