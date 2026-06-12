---
title: "Compiling emacs 22 on ubuntu 7.0.4"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2007-06-11
Hi,

I am trying to compile emacs 22 on ubuntu 7.0.4.  The compile completes, but when I execute the emacs, the tool bar icons/splashscreen only has black/white color.  Can you please tell me how to fix that? 

This is my configure string:
./configure --with-gtk -with-jpeg --with-png 

Thank you.

---

### Post by sinewalker on 2007-06-15
Hi yingcls

A wild stab in the dark here:  the colour icons are XPM files (explained in the Emacs Info manual, under Frames>Toolbars).  You might need to compile emacs with XPM support (--with-xpm perhaps?)

I mean to try this myself soon... ;)

---

### Post by octoberdan on 2007-06-21
You can always try the emacs-snapshot package until a stable version is released.

---

