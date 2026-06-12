---
title: "need re-install ubuntu edgy"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by ubuscout on 2007-01-26
Hi people,

time ago I 've installed ubuntu edgy 6.10 in dual boot (grub) on windows 2k machine...

Now I have installed ubuntu in a new computer and I need disinstall ubuntu in the first machine and restore the initial windows 2k in first machine...

How do it ?

thanks :)

---

### Post by housam on 2007-01-26
First back-up your files.
Using the Gparted you can reformat the ubuntu partitions and add the free space to windows partition .
This could lead to non-bootable windows due to the absence of grub. you can fix this by fixing the MBR from the windows CD or by using the [super grub disk ]("http://supergrub.forjamari.linex.org/")
Good luck

---

### Post by ubuscout on 2007-01-26
> **housam said:**
> First back-up your files.
Using the Gparted you can reformat the ubuntu partitions and add the free space to windows partition .
This could lead to non-bootable windows due to the absence of grub. you can fix this by fixing the MBR from the windows CD or by using the [super grub disk ]("http://supergrub.forjamari.linex.org/")
Good luck

Thx ...monday I'll try just arrive in office ! :)

...again thx !

---

### Post by ubuscout on 2007-01-29
It has work fine thx !  :D

---

