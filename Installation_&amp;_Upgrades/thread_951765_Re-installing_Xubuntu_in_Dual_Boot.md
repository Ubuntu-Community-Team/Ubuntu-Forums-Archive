---
title: "Re-installing Xubuntu in Dual Boot"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by pavan115 on 2008-10-18
Hello, I am very very new to linux. I have been playing with Xubuntu dual booted with XP for a while. When I change the screen resolution in Xubuntu it always crashes and I need to shut down and restart it :( But anyway, I want to reinstall Xubuntu and remove all instances of my old Xubuntu. I dont have much HD to spare :| How do I do this?

Also, GRUB shows two copies of the same thing (generic, recovery mode and so on..). Will this be fixed with a fresh install?

---

### Post by cariboo on 2008-10-18
If you need to reinstall, just install over top of the existing installation as the partitions get reformatted. The double entries in grub are just to different kernel versions.

You will be starting from scratch with a new installation.

Jim

---

### Post by pavan115 on 2008-10-18
> **cariboo907 said:**
> If you need to reinstall, just install over top of the existing installation as the partitions get reformatted. The double entries in grub are just to different kernel versions.

You will be starting from scratch with a new installation.

Jim
Thank you Jim,

I tried
> sudo apt-get install xubuntu-desktop 

and get

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


It still has not resolved my graphics problem. I have no data in Xubuntu that I am worried about, so I want to do a new installation replacing my Xubuntu. I have the live CD with me. How do I simply erase this xubuntu and reinstall it with default settings and everything on the same partition?

---

