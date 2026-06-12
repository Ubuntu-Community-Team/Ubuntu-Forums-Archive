---
title: "minimal custom install?"
date: 2004-11-19
forum: Installation &amp; Upgrades
---

### Post by oldi on 2004-11-19
I got the ubuntu Cd today and wanted to install it on my computer. I have only 1Gb hard disk with 64M memory. Since Ubuntu needs 1.8Gb for a full install i was wondering whether it is possible to do a minimal custom install. From what i saw, the installer doesn't give you that option. Is that right? Or am i missing something?

thanks

---

### Post by jdong on 2004-11-19
Boot with **custom-expert** (or expert-custom? don't remember now!)
 
 Anyway, it's on the **F-n** menus on the bootsplash for the CD. F3, perhaps!

---

### Post by az on 2004-11-19
Its there on the first page.  Type custom at the boot prompt.

This will install only a 350 base system.

Next, run aptitude and select ubuntu-desktop.  Before you tell it to go, find all (four) openoffice.org packages and deselect them.  Youwill be shown the amount of disk space that the install will consume at that point.  Remove more packages as neccessary...  You should be almost there...

( totem, and all the multimedia stuff would be a good bet, i guess, for more space recovery...)

---

### Post by oldi on 2004-11-20
Thanks for your answers. I have two more questions:

1. Is 64 Mb of memory enough to run Ubuntu? 

2. Is it possible to install ubuntu on two hd (RAID 0)? If yes can someone point me to the right direction how to do that?

Thanks

---

### Post by az on 2004-11-20
Yes, 64 megs is enough but more is better...

Raid is known as lvm in the installer.  Just use LVM (Ligical Volume Management) when you set up your partitions...

---

