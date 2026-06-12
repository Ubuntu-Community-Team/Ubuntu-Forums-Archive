---
title: "Ubuntu server display illegible symbols"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by Otterjasie on 2011-08-23
Hi All

I have installed Ubuntu server on my PC.  After booting up in Ubuntu server the text in the terminal/console is **completely** illegible.  To see a photo visit:

[http://serverfault.com/questions/286060/ubuntu-server-11-showing-weird-characters-on-console](http://serverfault.com/questions/286060/ubuntu-server-11-showing-weird-characters-on-console)

I have tried everything I could find on online (including the advice on the above website) forums but nothing works.  My PC specs are as follows:

CPU:                Intel Pentium III, 600MHz
RAM:                256MB
Graphics chip:   Intel 82810E, onboard

Do I have to post some command when installing Ubuntu?
Do I have to change the GRUB settings upon startup?
Do I have to use an earlier version of Ubuntu?

---

### Post by Earendil1982 on 2011-10-25
Same thing here since Natty using Ubuntu Desktop.
For Oneiric I did a complete reinstall, but the problem persists.

Any new clues?

Btw:
% LC_ALL=C lspci | grep -i vga
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
It's definitely not X, as it's running fine on my install and not part of a server install&#8230;
Kernel log will follow after the next regular boot, I'm suspending my machine most of the time

---

