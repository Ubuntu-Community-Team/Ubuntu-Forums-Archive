---
title: "How to dual boot FreeDOS and Ubuntu 6.10 in a virtual machine?"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by wiiwillwin08 on 2007-07-11
:confused:How do I dual boot FreeDOS and Ubuntu 6.10 in a virtual machine? I am confused!!:confused:

I have both FreeDOS and Ubuntu 6.10 ISO's.. Do I install FreeDOS first or Ubuntu?? Thanks for your help!:KS

And how do I partion them??

---

### Post by silverdarkness on 2007-07-12
1.make 2 partitions on your virtural disk using gparted on the ubuntu cd.
2.Install freedos first to one partition
3.Install ubuntu to the other partition.

i think grub will autodetect freedos, if it dosent then you can boot into ubuntu and add freedos to your grub menu manually.

---

### Post by wiiwillwin08 on 2007-07-13
> **silverdarkness said:**
>  if it dosent then you can boot into ubuntu and add freedos to your grub menu manually.
How do I manually do it?? (just wondering)

---

### Post by silverdarkness on 2007-09-29
edit the menu.lst and add the entry:

```

title FreeDos
rootnoverify (hdx,y)
makeactive
chainloader +1

```

change x,y depending on where FreeDos is installed

---

