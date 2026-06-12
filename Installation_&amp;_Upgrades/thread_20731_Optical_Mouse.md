---
title: "Optical Mouse"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by thys on 2005-03-18
I am totally new to Linux and I am overwheled by all the techical talk on all the forums! I have just installed Ubuntu but I cannot get my mouse working. The four button optical mouse on PS2 behaves erratically. When I replcae it with a standard PS2 Mouse, everything is fine.

What should I do?

---

### Post by GrapeApe on 2005-03-18
Optical mice work fine.  I use logitech optical's on all of my linux boxes.  What brand of mouse are you trying to use.  You may be picking the wrong protocol (in /etc/X11/XF86Config or xorg.conf).   Or it simply may not work well. 

If it is logitech, the ImPS/2 protocol works well.

Do a google search on the brand/model and XFree and see what pops up.

---

### Post by kuleali on 2005-03-18
You can configure the xorg.conf if you are in hoary
sudo gedit /etc/X11/xorg.conf

---

