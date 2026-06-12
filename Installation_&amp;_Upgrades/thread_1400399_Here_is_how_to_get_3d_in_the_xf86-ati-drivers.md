---
title: "Here is how to get 3d in the xf86-ati-drivers"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by mushwars on 2010-02-06
HOW TO GET 3d with the XF86-ati-driver

install from source the 2.6.32-r2 kernel
upgrade Xorg-server to 2.17.999
install from git libDRM-2.4.17
install from git mesa-7.7
install from git the xf86-ati-driver-9999

:popcorn:unless you **KNOW** what you are doing dont do this, you will also have to recompile KDE/gnome ( so I guess you have to install that from git as well )

ooo I forgot the reason why I posted this. Doing this is NOT worth it, I did it and when I went to play a 3d game it renders shadows poorly and some reflections are rendered upside down.

The reason why you are reading this is...
**If you want 3d accelleration with an ATI card, you MUST install the FGLRX proprietary driver.**

---

### Post by Mark Phelps on 2010-02-08
While it's really good that you provided so many cautions in your post (most folks don't do that), you should also mention that anyone with one of the "legacy" cards should also NOT try to install the fglrx drivers -- doing so will only hose up their display.

---

