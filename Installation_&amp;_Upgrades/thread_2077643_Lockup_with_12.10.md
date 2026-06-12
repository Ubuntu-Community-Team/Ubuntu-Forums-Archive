---
title: "Lockup with 12.10"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by gombosg on 2012-10-29
Hi!

The new Ubuntu 12.10 just locks up sometimes: after some ime (1 hour...1 day) the sound loops, mouse freezes, the computer does not respond. Only the reset button solves this problem.

I would say this is a memory fault, but I have never experineced this with either Windows or on 12.04 on this computer before the upgrade.

So far I haven't found any clues, signs of error in the following files:
[LIST]
[*]kern.log
[*]boot.log
[*]syslog
[/LIST]

I have attached those files. Just search for the string "*REBOOT*". (Turned on at 7:25, froze ad 7:44, and the computer has lost DST setting, thus it shows 8:44.)

Hardware:
Ubuntu 12.10 64 bit
MSI 770-C45
Athlon II X3 425
4Gb 1600MHz RAM
Ati 6770 1Gb (fglrx)

Thanks for your help in advance!

---

### Post by dino99 on 2012-10-29
is it a fresh install or a dist-upgrade ?
have you cleaned the system (clean/autoclean/autoremove/deborphan/bleachbit) ?

---

### Post by gombosg on 2012-10-30
Upgrade from 12.04 from 11.10. I'll try cleaning. :)

---

