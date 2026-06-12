---
title: "Ignorant Dual Boot"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by dingclancy on 2007-11-29
So I tried Ubuntu for the first time and was so impressed that I installed the live CD. Since I have an XP installed first, i knew that I need to dual boot. Stupidly, I just made a straightforward install assuming that Ubuntu will fix the dual boot for me. And I assumed wrong =(.


Now, XP won't show! all I see is Ubuntu. Please tell a newbie what to do. At this point, I'd rather uninstall Ubuntu now if it will bring back my XP since I need it for my work.

---

### Post by Pumalite on 2007-11-29
At the Terminal, post the output of:
sudo fdidk -lu

---

### Post by dingclancy on 2007-11-29
My Terminal

israel@israel-laptop:~$ sudo fdidk -lu
[sudo] password for israel:
sudo: fdidk: command not found
israel@israel-laptop:~$ 
israel@israel-laptop:~$

---

### Post by edwardTheGreat on 2007-11-29
he meant 
```
sudo fdisk -lu
```

---

### Post by dingclancy on 2007-11-29
```
israel@israel-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153340424    76670181   83  Linux
/dev/sda2       153340425   156296384     1477980    5  Extended
/dev/sda5       153340488   156296384     1477948+  82  Linux swap / Solaris
israel@israel-laptop:~$ 
israel@israel-laptop:~$ 
```


This is it

---

### Post by Pumalite on 2007-11-29
Windows is no more.

---

### Post by dingclancy on 2007-11-29
fork!!!
 Damn I just realized =(

Can anyone tel me how to instal XP with an Ubuntu on it already?

Thanks....

---

### Post by Pumalite on 2007-11-29
Use Gparted Live CD and make one large partition of your whole drive formatted ntfs. Then install XP.

---

### Post by dingclancy on 2007-11-29
Thanks Pumalite!

Your my first friend here hehe

---

