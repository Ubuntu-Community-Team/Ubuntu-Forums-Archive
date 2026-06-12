---
title: "ATI 8.42.3 still mesa on fglrxinfo"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by templarrush on 2007-12-09
I just installed the new ATI driver 8.42.3 with AIGXL
And now I get the mesa things when I enter fglrxinfo in the terminal

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

When I try to enable Compiz my screens goes white.
Anyone has a solution to solve this?

I've read these things solve it but the first command gives an error already

$ sudo rmmod fglrx
$ cd /lib/modules/*/misc
$ sudo insmod fglrx.ko
$ modprobe fglrx

---

