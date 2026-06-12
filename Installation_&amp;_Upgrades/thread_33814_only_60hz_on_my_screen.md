---
title: "only 60hz on my screen"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by futte on 2005-05-12
Why kan i not use 1200*1024 85hz but only 60hz "Unbutu"  :roll:

---

### Post by Stormy Eyes on 2005-05-12
[QUOTE=futte]Why kan i not use 1200*1024 85hz but only 60hz "Unbutu"  :roll:[/QUOTE]

Ubuntu, for some reason, likes to use "safe" settings when automatically configuring the X Window System. If you want to push your display to its maximum, you'll have to dig out the manual for your display, refer to the vertical and horizontal sync rates, and manually hack /etc/X11/xorg.conf. The settings you want are in the "Monitor" section and are called "HorizSync" and "VertRefresh".

---

