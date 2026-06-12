---
title: "GM45 intel 4500 3D accel is unavailable in jaunty"
date: 2008-12-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by linibird on 2008-12-14
Hoping the latest version would help me from new hardware headaches, I just installed Jaunty on my thinkpad x200. Networking works out of the box. 1280x800 resolution is also OK without a xorg.conf. I see intel driver,dri,drm are working from the log. But 3D accel always fails. I tried quake 3 and glxutils. These apps all reports they are using software accel-ed mesa drivers. Jaunty mesa version is 7.3-devel. I downloaded a mesa version(7.2). It didn't help either.

glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x80bf008
  Window:      0x1e00002
  Context:     0x80c8260
  GL_VERSION:  2.1 Mesa 7.2
  GL_VENDOR:   Brian Paul
  GL_RENDERER: Mesa X11


Please help. Xorg.0.log is attached. Thanks a lot.

---

### Post by cb951303 on 2008-12-14
> **linibird said:**
> Hoping the latest version would help me from new hardware headaches, I just installed Jaunty on my thinkpad x200. Networking works out of the box. 1280x800 resolution is also OK without a xorg.conf. I see intel driver,dri,drm are working from the log. But 3D accel always fails. I tried quake 3 and glxutils. These apps all reports they are using software accel-ed mesa drivers. Jaunty mesa version is 7.3-devel. I downloaded a mesa version(7.2). It didn't help either.

glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x80bf008
  Window:      0x1e00002
  Context:     0x80c8260
  GL_VERSION:  2.1 Mesa 7.2
  GL_VENDOR:   Brian Paul
  GL_RENDERER: Mesa X11


Please help. Xorg.0.log is attached. Thanks a lot.

everything will get better for intel drivers once dri2 and gem is integrated to the kernel (which is soon)

---

### Post by linibird on 2008-12-14
But how can I solve it now? Is there a version of kernel in development that includes all you said?

> **cb951303 said:**
> everything will get better for intel drivers once dri2 and gem is integrated to the kernel (which is soon)

---

