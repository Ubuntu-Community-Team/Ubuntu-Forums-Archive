---
title: "Install ATI drivers - Ubuntu 10.10"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by sim0s on 2010-11-29
Hello guys.......

I have an ATI Mobility Radeon x1800 graphic card and I am trying to install it to Ubuntu 10.10.
I managed to install Ubuntu with nomodeset but the resolution was very bad and that's why I am trying to install the ATI drivers.
I have deleted the xorg.conf file, installed the ati drivers through package manager and changed nomodeset to radeon.modeset=1  but when I am trying the commands **glxinfo | grep render **and **glxinfo | grep vendor **they don't shown the ATI drivers... and the resolution is still bad.

Does anyone what to do?
I am providing the results for the 2 commands above.


```

spy@Spy:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Mesa Project
spy@Spy:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 
spy@Spy:~$ 


```

---

### Post by Mark Phelps on 2010-11-30
There are no ATI proprietary drivers that will work with your card and current versions of Ubuntu.  AMD/ATI dropped proprietary driver support for you card a long time ago.

The only drivers that will work now are the open-source drivers -- and they are already installed.

IF you download or otherwise force the installation of any other drivers, you will trash your display and have to spend a LOT of time cleaning up the resulting mess.

---

### Post by shadowlemon on 2010-12-01
> **Mark Phelps said:**
> There are no ATI proprietary drivers that will work with your card and current versions of Ubuntu.  AMD/ATI dropped proprietary driver support for you card a long time ago.

The only drivers that will work now are the open-source drivers -- and they are already installed.

IF you download or otherwise force the installation of any other drivers, you will trash your display and have to spend a LOT of time cleaning up the resulting mess.

Would this also apply for ATI Mobility Radeon 3650HD?
Right now, compiz works, native resolution, even some 3D programs work just fine, however games run terribly slow, that's why i was wondering.

---

