---
title: "How to set vga values?"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by kma711 on 2011-02-05
Getting half of a screen with big fonts :confused:

---

### Post by dino99 on 2011-02-05
are too lazy to give your config, i cant guess which it is :(

actually, kernel directly deal with X, so remove xorg.conf:

sudo rm /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by kma711 on 2011-02-07
I am a newbie and just able to get into terminal. I am having problems at start up. Fonts are very big and I am getting the bottom half of my screen as black.

---

