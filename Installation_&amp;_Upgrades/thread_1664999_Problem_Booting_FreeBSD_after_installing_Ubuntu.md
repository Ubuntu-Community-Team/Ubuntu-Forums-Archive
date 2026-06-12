---
title: "Problem Booting FreeBSD after installing Ubuntu"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by M-D-M-A on 2011-01-11
Hello everyone, I hope someone can help me with this...
 
I partitioned my HD in 4 so i could install FreeBSD, Windows, MacOS, ans Linux in this order
so the first partition has FreeBSD the second has Windows 7 the third MacOS and the fourth Ubuntu

the problem is after i instaled Ubuntu

i can see and boot into every OS except FreeBSD
anyone know why??
thanks in advanced

---

### Post by M-D-M-A on 2011-01-11
just wanted to let you all know that i got it
all i had to do was
edit the /etc/grub.d/40_custom file
i added :

menuentry "FreeBSD 8.1" {
set root='(hd0,1)'
chainloader +1
}

then i ran : sudo update-grub

and it worked :D:D:D

---

