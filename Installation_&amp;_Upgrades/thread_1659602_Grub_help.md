---
title: "Grub help"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Zors on 2011-01-04
Hi, new to linux here.
I have 2 hard drives:
HD1 has windows 7
HD2 has ubuntu

When I installed ubuntu though, I had HD1 plugged out.
Now, whenever I want to boot into ubuntu, I need to go to boot menu on my BIOS.

Is there a way to change this so I can just choose which operating system, with default being windows 7?

Thx

---

### Post by dino99 on 2011-01-04
welcome,

you might have installed grub right ? You need to update its menu (both hdds plugged) by running this command into a terminal (Applications Accessories Terminal):

sudo update-grub

---

### Post by Bucky Ball on 2011-01-04
> **dino99 said:**
> welcome,



sudo update-grub

+1

---

### Post by Zors on 2011-01-04
Thank you :D
I got another question if you dont mind
its at the bottom of [http://ubuntuforums.org/showthread.php?p=10315474](http://ubuntuforums.org/showthread.php?p=10315474)

Thanks again for the quick replies

---

### Post by drs305 on 2011-01-04
Once Grub2 has found the Windows entry, you have to set it as the default.

This link will take you to a guide to show you how to do that.
[Grub 2 - 5 Common Task]("http://ubuntuforums.org/showthread.php?t=1302743")

You can also use StartUp-Manager, a GUI app, to set the default. See the "SUM" link in my signature line.

---

