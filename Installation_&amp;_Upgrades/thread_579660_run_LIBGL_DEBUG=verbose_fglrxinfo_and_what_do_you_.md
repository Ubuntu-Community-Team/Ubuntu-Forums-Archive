---
title: "run LIBGL_DEBUG=verbose fglrxinfo and what do you get?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2007-10-18
libGL error: XF86DRIQueryDirectRenderingCapable failed

anyway to make it work?

scott@scott-desktop:~$ LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.40.4 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.40.4 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/scott/.drirc: No such file or directory.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6747 (8.40.4)

scott@scott-desktop:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 1.2 (2.0.6747 (8.40.4))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
scott@scott-desktop:~$

---

### Post by jimerickso on 2007-10-18
are you using xgl?? DRI does NOT work with XGL! sorry!

---

### Post by sdowney717 on 2007-10-18
how would you not use xgl.?
I upgraded to gutsy and that is what it seems to be using.

so what do I do?

---

### Post by jimerickso on 2007-10-19
on gutsy you have to install xgl to make it use it:

sudo apt-get installl xserver-xgl

then it will run whenever you log into your x session. you will have to have xgl if you are trying to get compiz-fusion running. as far as fglrx is concerned just wait till next week when the new one is released and you won't have to have xgl anymore as it will use aiglx. hope that helps!

---

