---
title: "Radeon 4550 black 3D / no Unity despite reporting 3D being ok"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by pontu on 2011-05-01
MSI P4M890M, 512M RAM
Gigabyte HD4550 512M

1. after install i got blank wallpaper+mouse (auto login)
2. learning to Ctrl+Alt+F1 and pkill X gave me login screen where Safe Mode got me in sans Unity
3. $ /usr/lib/nux/unity_support_test -p```

OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```4. glxgears (and tuxracer) produce black window with no graphics, similarly no FPS output to console, going deeper:
5. $ vblank_mode=0 glxgears ```
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
2 frames in 11.9 seconds =  0.167 FPS
1 frames in 6.5 seconds =  0.154 FPS
1 frames in 6.0 seconds =  0.166 FPS
1 frames in 5.5 seconds =  0.182 FPS
1 frames in 6.0 seconds =  0.166 FPS
1 frames in 6.0 seconds =  0.167 FPS
1 frames in 6.0 seconds =  0.166 FPS
1 frames in 6.0 seconds =  0.166 FPS

```6. both radeon and fglrx seem equally crippled (direct rendering: Yes)

help:confused:

---

### Post by Sinner on 2011-07-13
Up please.

---

### Post by OS1 on 2011-10-13
Same here, everything suggests that 3D should work but it just doesn't. DRI & DRM enabled just fine, glxinfo reports Direct Rendering is enabled, no errors in the xorg log file, yet still no 3D. glxgears report about 10 fps. I did see this kind of behaviour on a Mandriva install when there were permissions problems so I tried an xorg.conf that had a DRI section but still no good. What on earth do I need to do to get 3D running when it worked just fine in 10.04. I think it may have actually have broken in 10.10 but I only used this as an upgrade path to 11.04. Has the ATI driver been "improved"? How could I revert to the 10.04 drivers?

---

