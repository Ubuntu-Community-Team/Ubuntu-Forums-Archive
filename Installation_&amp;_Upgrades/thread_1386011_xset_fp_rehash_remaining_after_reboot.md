---
title: "xset fp rehash remaining after reboot"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by RicoUK on 2010-01-20
Hi,
 
I have a program which uses it's own fonts.
I have created a link under /usr/share/fonts to the directory where they are installed to.
I ran mkfontdir /usr/share/fonts/t32
 
My application failed to start because a font was missing.
 
I ran:
 
xset +fp /usr/share/fonts/t32
xset fp rehash
 
and everything worked.
 
However, after a reboot I have to manually enter the xset commands again to re-register the fonts with my system.
 
What is the approvedc method of installing fonts permanently?
 
TIA,
 
RicoUK

---

