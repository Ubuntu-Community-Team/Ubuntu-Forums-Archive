---
title: "[SOLVED] No Edgy on nForce430 with GeForce6100 on board"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by siddartha on 2007-01-18
I just bought a new system with an Asus M2N-MX motherboard and Edgy refuses to even start up the live CD. I downloaded the other day the destktop iso image for 6.10 and burned it on a CD. I goes most of the start up at at a point it stops the mouse (PS/2) and the screen flashes from time to time while the CD led is lit meaning its working. I thought the CD was broken somehow so I got another blank CD, burned the image, verified the image with the function from k3b and everything was ok. The exact same problem. With normal startup it breaks before the gnome splash screen - no mouse or keyboard reaction. With failsafe (second option) it shows a mouse cursor on a light brown screen (no flashing also) and I can change to the first console where I can issue a command with no results (I can't even suspend or stop the command after that).

What am I doing wrong?

---

### Post by siddartha on 2007-01-28
The problem stands with the video card detection - it tries to use the free nv x server as it guesses that is a nVidia card but nv doesn't work. Vesa works.

---

