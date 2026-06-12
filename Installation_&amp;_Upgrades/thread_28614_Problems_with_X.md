---
title: "Problems with X"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by Seldon on 2005-04-20
Hi, im kind of new in this linux world and Im trying to install Ubuntu. I first tried qith the flash cd and no problem, everything run perfect but then I installed it and when I run it for the first time it said there was a problem with x configuration and only let me enter to a terminal.

Please help me :P

PD: sorry for the bad english, it is not my first language

---

### Post by diebels on 2005-04-20
Post /var/log/XFree86.0.log and /etc/X11/XF86Config.
Inside [CODE] tags

---

### Post by Seldon on 2005-04-21
sorry, can you be more specific, an explanation like you did it for a estupid person :P

---

### Post by diebels on 2005-04-22
To diagnose your problem we need the contents of the files I mentioned. But you could always try to just type in "dpkg-reconfigure xserver-xorg"[ENTER], follow the instructions, and choose a safe driver like "vesa". Will probably fix it, but will be slow.

Oh, if you are using warty, type in:
"dpkg-reconfigure xserver-xfree86"[ENTER]

---

### Post by Seldon on 2005-04-23
I tryed with both comands and the didnt work, it said there is a conflic with the options.

I also tryed to open the file you mentiones with vi and it said that it was a new file and just open an empty document.

Please help :P

---

