---
title: "Screen size problems - How to set to 1024x768?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by claudio64 on 2008-04-27
Hi,

I installed 8.04 in my laptop using wubi and I have a problems with screen size.

The logon box appers at botton-right side of my screen as using virtual screen but without be able to scroll the screen down or right.

After login I can see part of the wallpaper but nothing about the KDE menu bar.

Scrolling the mouse pointer to down-left till it disappers and clicking, I got the two last options of the menu (virtual screen again).

I reboot and use the safe mode to try to repair the xorg.conf files using vi (blagh!). The xorf is completely new and don't indicate the driver to load.

I include "Driver vesa" on Device section and X server crashed.

My labtop has a S3 video board.

How can I define 1024 x 768 as my default screen size?

---

### Post by claudio64 on 2008-04-27
Hi,
 
Problem solved with:
1) boot safe made
2) log as root
3) edit xorg.conf using vim
4) included subsection Display @ Screen.

Bye!

---

