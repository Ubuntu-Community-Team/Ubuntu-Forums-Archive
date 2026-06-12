---
title: "Ubuntu boots to a text login, no X or startx"
date: 2005-09-16
forum: Installation &amp; Upgrades
---

### Post by kimballj on 2005-09-16
I just installed ubuntu using the netboot on a laptop w/out a working CD drive.  Install worked fine but when I boot I don't get X, I just get a text login.  Furthermore, when I type "startx" I get a "command not found"

I checked and the /ect/X11/xorg.config is there and the values seem right (detected my correct video card) but startx does't exit.

Any thoughts?

I tried apt-get install xorg-common and apt-get install xorg-driver-fglrx and both are up to date.

---

