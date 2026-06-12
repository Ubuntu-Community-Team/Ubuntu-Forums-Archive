---
title: "grub is corrupt, but ctrl-alt-delete boots to my mysterious partition!"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by uclabuntu on 2007-09-06
ubuntu was installed on hda7.  i've tried setting up grub on (hd0,6), and i've tried the /find/boot/stage1 commands and whatnot to help out.  i get error 17... and for one partition, it just fails to boot up and tells me that apt isn't installed (try apt-get apt  lol).

anyway, when i'm presented with this apt-get apt dismal screen, i press ctrl-alt-delete, thinking it'll restart my computer.  HOWEVER, it boots up to my correct partition with all my files!!! i've tried booting from all the listed options under grub, but all fails.

anyone know how to get grub to recognize what this magical partition is?  (p.s. win xp is unfortunately installed on hd0,0

thanks!

---

### Post by meierfra on 2007-09-07
Post the output of

```
sudo fdisk -l
```
( the l is a lower case L)

and

```
cat /boot/grub/menu.lst
```

---

