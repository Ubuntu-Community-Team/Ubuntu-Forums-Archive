---
title: "X Problems with Hoary Upgrade (Radeon 7000)"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by rmjokers on 2005-04-14
After upgrading from Warty to Hoary using apt-get, X would freeze during the loading process for gnome, xfce and fluxbox.  I tried reconfiguring the X server but it did not seem to help.  However, I found that if I comment out the following lines in my
/etc/X11/xorg.conf file, the X server does not freeze:

        #Load   "dri"
        #Load   "glx"

There must be a driver issue with the radeon driver or a problem with the configuration application.  Anyways, just thought people might want to know how to fix this problem.  Anybody know where I can report this so it gets fixed in future releases of Ubuntu?

---

