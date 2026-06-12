---
title: "Switch"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by nrs on 2006-11-08
Hello, 

I had an nVidia 6600GT with which I was using the beta proprietary drivers. I recently had to switch back to my Radeon 9600XT. 

Of course, I have no GLX extension: 

>  cat /var/log/Xorg.0.log | grep -i glx


> (II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
(II) Loading extension GLX
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Does anyone know which package I could re-install to get a compatible libglx.so ?

---

