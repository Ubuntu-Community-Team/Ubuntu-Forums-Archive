---
title: "XFCE4 resolution problem"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by sgoen1986 on 2006-04-23
After some help from this forums I got Ubuntu server installl done and running XFCE4.

Still I have a minor problem, which is I cant change my resolution, so I'm stucked here with a 640x480 desktop, not very beautiful.

Please help me solve this.
Thanks!

---

### Post by stuporglue on 2006-04-23
In a terminal or console, run:

sudo dpkg-reconfigure xserver-xorg

Follow prompts, then:

sudo /etc/init.d/gdm restart

---

