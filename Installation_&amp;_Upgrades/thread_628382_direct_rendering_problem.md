---
title: "direct rendering problem"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by adamb23 on 2007-12-01
ok i have installed the newest driver for the ati radeon 9800 pro for ubuntu gutsy 7.10.  when i check to see if the direct rendering works using this command glxinfo | grep direct i get this message 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

anyone know how to fix this?

---

### Post by leomelo on 2007-12-01
Try this:in synaptic, uncheck all the xserver-xorg-video boxes and only let checked the xserver-xorg-video-ati checked.

---

### Post by adamb23 on 2007-12-01
theres the green and white ones should they all be white or green exept for ati?

---

