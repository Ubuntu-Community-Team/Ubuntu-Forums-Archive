---
title: "Cannot install ubuntu on EliteBook 755 g5"
date: 2018-09-09
forum: Installation &amp; Upgrades
---

### Post by thepixelbro on 2018-09-09
Hey guys, I finally got my EliteBook 755 g5 and excited to start setting up as my work station, but it seems that i cannot install ubuntu at all, or any linux distro because it would never go bast UEIF boot screen.

So this is how it goes.

1. Boot into Ubuntu 18.04.1 installation media

2.Shows me the Grub boot menu

3. Select install Ubuntu

4. Black screen nothing happens.

I made sure to disable all bios boot security, but still nothing happens, so I think something on hp side is stopping it from booting,

Please help guys, you're my only hope.

---

### Post by ubfan1 on 2018-09-10
Did you try the "Try Ubuntu" option on the boot media?  Many times a video problem may occur, resulting in a black screen, so it may be necessary to edit the grub commands (type e to edit, instructions at bottom of screen), and do things like add the word "nomodeset" at the "quiet splash" words.  More information about your hardware may help us make suggestions.

---

### Post by atanas.m on 2018-09-20
This may help you:
[https://askubuntu.com/questions/1064842/hp-elitebook-745-g5-install-ubuntu18-failrestart-usually-fail-sometimes-ok](https://askubuntu.com/questions/1064842/hp-elitebook-745-g5-install-ubuntu18-failrestart-usually-fail-sometimes-ok)

Do you have any progress :)

---

