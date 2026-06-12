---
title: "Problems installing Gutsy with a PCI IDE card"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by BuhSnarf on 2007-11-22
Hi,

My new motherboard only has 1 IDE channel so I've had to install a PCI card with 2 extra IDE channels.

Ubuntu is my primary OS but I also have WIndows to play some games.

Setup is currently.

Motherboard IDE
1 ) 80GB HDD containing Windows
2 ) CD ROM

PCI Card
1 ) 120GB HDD with Ubuntu
3 ) CD ROM

I've put Ubuntu on the PCI so that it can use Grub to boot between Windows/Ubuntu as I figured that handle it better than Windows. However, after installing Ubuntu and restarting when it boots off Grub at the beginning of the 80GB drive it gives the dreaded Error 17 and then hangs.

Does anyone have any idea what might be up?

Cheers.

---

### Post by meierfra on 2007-11-23
Grub sometimes gets the two hard drives confused.

 Do you get error 17 before the grub menu appears? Or after you select ubuntu from the grub menu?

Boot from the LiveCD, mount your ubuntu partition to say the directory gutsy (let me know if you need help with that) and  post the output of


```
sudo fdisk -l
```
and
```
cat gutsy/boot/grub/menu.lst
```

(both "l" are lower case L, not the number one):popcorn:

---

