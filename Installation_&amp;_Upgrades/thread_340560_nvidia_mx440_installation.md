---
title: "nvidia mx440 installation"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by ion one on 2007-01-17
I'm using Nvidia GeForce MX440 and i want to install the latest drivers and i'm experiencing problems when installing from [www.nvidia.com](www.nvidia.com) when installing the driver 96xx it always installs the driver for 96xx but the kernel for 7xxx (don't remember the numbers)..please help!i'm sure a lot of other geforce 4 users experience this problem..i'm using ubuntu edgy with amd athlon xp 1600+ 256 ddr 64 vram..thanks in advance!

---

### Post by ion one on 2007-01-17
oh and during the installer gives me "coulnd't not find matching kernel (...) would you like to download the kernel at ...." and i say yes and it says that coulnd't find one and is gonna build one itself ... and it builds the wrong one (for 7xxx not for 96xx)

---

### Post by allwin on 2007-01-17
> **ion one said:**
> oh and during the installer gives me "coulnd't not find matching kernel (...) would you like to download the kernel at ...." and i say yes and it says that coulnd't find one and is gonna build one itself ... and it builds the wrong one (for 7xxx not for 96xx)
Not saying this is ultimately going to work, but try ENVY at this guy's page:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And if you install it and it works, remember that it is around because I have found that frequently automatic updates blow away the underpinnings of the proprietary nVidia drivers and your X won't start!  If that should happen to you in the future, you then can just run ENVY while in terminal mode, sit there, and the drivers and other stuff are automagically re-installed.  PITA, but it works.  Also good to have ENVY sitting around if you are going to mess with Beryl.

---

### Post by ion one on 2007-01-19
the same thing!can any1 tell me where to find the kernel for 96xx or a hint?

---

