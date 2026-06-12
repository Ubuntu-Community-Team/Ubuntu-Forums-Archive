---
title: "Can't uninstall Ubunutu"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by VaporWare on 2012-02-07
I installed ubuntu inside windows on my computer, to learn C++. I'm taking it really slow so I can learn and  memorize at a good pace. Anyways, recently I bought a AMD Fx-8120. I'm sure you can imagine the excitement that came over me when I decided it was time to drop it in. Well, I was so excited, I forgot to uninstall ubuntu. Now the ubuntu uninstaller won't start, nor will wubi. Any ideas on an alternate way to uninstall ubuntu, or fix the uinstaller so I can?
I am using windows 7.

---

### Post by ottosykora on 2012-02-07
which windows version?

in fact one can just remove the virtual disk(s) where ubuntu is stored and the remove the entry in the bootmanager of windows, like delete the line with ubuntu in boot.ini in XP for example

---

### Post by Mark Phelps on 2012-02-08
The wubi file to be removed is named root.disk.

If you're uncomfortable messing around with the windows boot loader by hand, and you're running Vista or Win7, then download and install EasyBCD from the Neosmart Technology forums -- and use it to remove the Ubuntu boot loader entry.

If you're running XP, all you have to do is open Notepad and remove the Ubuntu line from boot.ini.

---

### Post by VaporWare on 2012-02-09
Thankyou for the help guys.

---

