---
title: "plz help"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by usien on 2006-12-23
i am totally new to linux nd ubuntu.i downloaded ubuntu 6.10 livecd and after evaluating i decided 2 install it.wen i installed it the GRUB didnt by default detect my previous windows xp installation.i tried to add the following to menu.lst but wen i run this entry it says 'invalid device requested' or 'non executable format' :

title Windows XP
root(hd0,1)
makeactive
chainloader +1

i also tried changing (hd0,1) to all the partitions there r (e.g (hd0,2) (hd0,3) nd so on), but still the same error. can anyone help

---

### Post by bulldog on 2006-12-23
Can you give us the outcome of ```
sudo fdisk -l (l as in like)
```
And your menu.lst as well please ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by meng on 2006-12-23
There's also (hd0,0)
Also, I dunno if it makes a difference, but did you put a space between root and (hd..)?

---

