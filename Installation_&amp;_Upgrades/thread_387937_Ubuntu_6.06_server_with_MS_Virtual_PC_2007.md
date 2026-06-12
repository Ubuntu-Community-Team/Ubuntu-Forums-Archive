---
title: "Ubuntu 6.06 server with MS Virtual PC 2007"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by MMiller1028 on 2007-03-18
The font changes during the boot process and no longer fits inside the virtual pc window.  Recovery mode works find and the font remains readable.  I have tried changing some of the settings in the console-tools/config file but I haven’t had any luck.  I am hoping that someone can help me out.  Should I change the font in the config file? And if so to what?  

[IMG]http://img138.imageshack.us/img138/2258/screenjotcropped0318200nq6.jpg[/IMG]

---

### Post by MMiller1028 on 2007-03-20
I found that if I removed the boot options of (quiet,splash) in the menu.lst file the font remains readable.  I will only be using it text mode anyhow so this seems to work.

---

