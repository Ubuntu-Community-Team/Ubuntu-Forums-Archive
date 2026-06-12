---
title: "Help with ATI Video Drivers."
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by andy- on 2007-02-02
I've installed the repositories, which worked fine except for one thing I couldn't change resolutions / refresh rates. Hour later after messing around with it, I ended up installing the drivers from ATI.AMD.com which didn't change a single thing and even made things worse by removing the ATI driver I had installed from repositories. Anyway to make long story short, this is my current fglrxinfo output:

andy@home:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

andy@home:~$

I got resolutions / refresh rates fixed and working, I just need to get normal ati drivers working again, and everything is allready installed, I don't know how to go back to it. Help please :(

---

### Post by pay on 2007-02-02
Well the fglrx driver isn't setup correctly. To fix that follow [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide). If you want to change back to the previous driver, open /etc/X11/xorg.conf and look for Section "Device" and change the driver to "ati".
Goodluck.

---

