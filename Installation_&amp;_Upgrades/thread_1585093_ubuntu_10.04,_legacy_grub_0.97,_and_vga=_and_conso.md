---
title: "ubuntu 10.04, legacy grub 0.97, and vga= and console resolution"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by kamuz on 2010-09-30
Hello

I upgraded from 9.04 to 10.04.1 so I am still using legacy grub.

Anyway, I noticed with the update that the console is using the framebuffer and using VESA for high resolutions.

I really don't like or want this feature. So I added vga=0 to get 80x25 and it works initially but just when the X server is running (Xubuntu in my case) I can see how the console switches to a high resolution again. After this, if I go to a console, lets say tty1, it is using again a high resolution instead of 80x25 (VGA).

Is there a way to force the consoles to be in a lower resolution? It used to work fine in ubuntu 8 and 9


Thanks.

---

