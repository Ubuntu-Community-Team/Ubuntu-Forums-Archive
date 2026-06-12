---
title: "update-initramfs error"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-17
```
~$ sudo update-initramfs -c -k all
update-initramfs: Generating /boot/initrd.img-2.6.32-999-generic
rm: cannot remove `/tmp/mkinitramfs_zaYNax/lib/modules/2.6.32-999-generic/modules.*map': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.32-8-generic
rm: cannot remove `/tmp/mkinitramfs_XsGm0A/lib/modules/2.6.32-8-generic/modules.*map': No such file or directory
```
It seems it makes initrd files OK ...

---

### Post by autocrosser on 2009-12-17
I just saw this---interesting enough that I got that also just before I rebooted & ran into my ["little" problem]("http://ubuntuforums.org/showthread.php?t=1357117").....

---

