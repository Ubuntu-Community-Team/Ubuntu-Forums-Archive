---
title: "X starts up but no display"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by viisii on 2005-12-03
Hi all.

I have a slight problem after installing Breezy Badger for AMD64. From what I can tell, when booting up X starts but all I get is a non blinking cursor in the top left of the screen. I do have hard drive activity for a short time during this and whats more, once this is done I get sound(gnome sounds) when hitting buttons or clicking around with my mouse.This leads me to believe that gnome does start correctly. I have googled around but can't find any help on this issue.
Any advice would be much appreciated.

My Setup: K8NXP-SLI - Gigabyte 3D1 Dual Core 6600GT - 3800 x2 64 - LCD Monitor running of DVI.

PS. My mate has the same Motherboard and Graphics card and he has the exact same problem trying to run it on a CRT monitor.

Thanks.

---

### Post by newuser111 on 2005-12-04
do **sudo dpkg-reconfigure xserver-xorg** press ctrl-alt-f1 to get into console if you need to

and chose vesa driver

then use easyubuntu

[http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta](http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta)

and install the nvidia driver

---

