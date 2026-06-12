---
title: "Screen corruption in Ubuntu 8.04"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by OMA2k on 2008-05-10
Hello, I've tried to install Ubuntu 8.04 but after rebooting, I got a corrupted screen. I get the same if I just boot the LiveCD. After the Ubuntu boot logo showing up, a "psychodelic screen" appears (see attached image).

I suppose it's some issue with my graphics card. It's a nVidia TI 4200 manufactured by Creative. Is there some way to get this working?

---

### Post by Pumalite on 2008-05-10
Try the Alternate CD.

---

### Post by OMA2k on 2008-05-11
That doesn't work either :(
It's not a problem with the Live CD but something related with the graphics drivers, I suppose.

The odd thing is that older versions of Ubuntu worked fine in this machine.

---

### Post by lswest on 2008-05-11
boot up into recovery mode (hit "esc" when the grub menu is loading, then choose the second entry) (then choose a root shell) and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and see if that brings you to a GUI, since you said you installed it?

---

