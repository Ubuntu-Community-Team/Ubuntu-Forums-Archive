---
title: "Can I dual boot and keep Windows loader???"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by timstone on 2010-03-21
I have Windows 7 on my machine right now but want to dual boot with either Ubuntu or another Win OS.....is there a way to dual boot with ubuntu and keep my windows boot loader or do I need to have grub?

---

### Post by stlsaint on 2010-03-21
Unless you have two harddrives and you use one for ubuntu and one for windows than you will need use grub. Windows bootloader will not see the ubuntu install.

---

### Post by timstone on 2010-03-21
I actually do have 2 hard drives...both installs will be on seperate drives....is there a writeup somewhere?

---

### Post by stlsaint on 2010-03-21
Just install windows on your master hdd...then remove it from system then install ubuntu on second hdd and the plug first hdd back in. Make sure that the master hdd is the one that is set to boot first in bios and that is the one with windows on it. Then when you want to boot ubuntu just go into bios and select the second hdd to boot from.

---

### Post by timstone on 2010-03-21
MEH...that seems like too much trouble...maybe I'll just use the grub loader

---

### Post by raymondh on 2010-03-21
edit : op decided to do a wubi install

[http://ubuntuforums.org/showthread.php?t=1435803](http://ubuntuforums.org/showthread.php?t=1435803)

---

