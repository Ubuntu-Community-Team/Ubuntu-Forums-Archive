---
title: "direct rendering issue"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by adamb23 on 2007-12-21
im using an ati 9800 pro graphics card on gutsy gibbon. I recently did a fresh install and had gotten everything to work, direct rendering and all until i enabled 3d desktop effects and rebooted. Now when i run LIBGL_DEBUG=verbose glxinfo i get the following error. 

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
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
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

if anyone could help i would appreciate it.

---

### Post by RIchard James13 on 2007-12-21
Have you followed the steps on this page?
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Skip the method 2 section and go to the "Configure the Driver" section and work your way down.

Also by what method did you configure your xorg.conf file?

Are you using AIGLX?

How did you enable 3D effects? What steps did you take?

---

### Post by erfahren on 2007-12-21
actually, I think that might be normal to show that you *don't* have direct rendering when using XGL and the fglrx driver. I can't remember why, but I seem remember that being the case.

fresh install here (Feisty) as well and haven't set up xgl yet so I can't verify that, maybe another ATI user using the proprietary driver and xgl on Gutsy can can verify that.

do your desktop effects (Compiz Fusion) enable and work normally?

**EDIT:**  just realized what I wrote... I meant to say that's it's normal to show that you *don't* have direct rendering. 

I aplogize for that. hope it didn't cause much confusion. (I need to proofread what I write more!)

---

### Post by RIchard James13 on 2007-12-22
I'm using 
Gutsy 7.10
Radeon 9600 LE
ATI Driver 7-11(installed via method two on that page)
Compiz
Not using XGL server

Compiz works but some OpenGL games have trouble, crack attack has no Window borders/title most games still flicker despite the command "export XLIB_SKIP_ARGB_VISUALS=1" being run before them.  I did not have this problem with my previous configuration with the ATI 8.42.3 driver. But since then I have changed motherboards and graphics (ATI-NVIDIA-ATI) cards in and out of machine which breaks everything, plus I used the XGL server. I have a new NVIDIA card AGP 7600 that I will install next week to see if I can get user switching to work with 3D acceleration because at the moment for me it is broken with my Radeon card. 

But compiz works at the moment but OpenGL for me is broken probably due to either that specific driver or a setting in my xorg.conf file. I did have compiz and OpenGL both working previously on my Radeon 9600.

---

### Post by erfahren on 2007-12-22
ok, I got my XGL set up and have my Compiz-Fusion enabled - I'm using the fglrx driver (8.34.8) included with Feisty.

before I installed XGL and booted into the session I got the output from "glxinfo | grep direct" as "Direct Rendering: Yes"

now that I'm using xgl it's
```

erfahren@acer-ubuntu:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

As I mentioned, I don't recall why that is but I think it's normal with xgl.

---

### Post by twist2b on 2007-12-22
yea xgl suks..... did you do the official compiz install? also did you download the extra plugins for compiz? that could be the problem.... how did you download compiz? theres a few out there that screwed me up... but the official guide from compiz's site was the trick and i was fine there after.

---

### Post by erfahren on 2007-12-22
> **twist2b said:**
> yea xgl suks..... did you do the official compiz install? also did you download the extra plugins for compiz? that could be the problem.... how did you download compiz? theres a few out there that screwed me up... but the official guide from compiz's site was the trick and i was fine there after.
I guess you were replying to my post.

for Feisty I use a combination of these HowTos:
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

and have a little script to start Compiz with a delay.

In my first post here I meant to reply to the OP that it showing as *not* having direct rendering with xgl was normal, as I recalled. (I screwed it up and  had to go back and edit it.)

my install works well and is pretty stable (all things considered).

---

### Post by RIchard James13 on 2007-12-23
I thought I would try the server-xgl again. This is the result.
```

$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

Of course the verbose mode tells nothing is wrong except it is using MESA (Software OpenGL). Also some of my tray applets crash, I have no trash can or volume control.

I am going to try the previous ATI driver the 8.42.3 version

---

### Post by RIchard James13 on 2007-12-23
> **RIchard James13 said:**
> I am going to try the previous ATI driver the 8.42.3 version

Ok that was a big mistake on my part. Now I've lost 3D graphics all together whether I use the latest driver or the 8.42.3 one. When I enable 3D in my xorg.conf and after the desktop loads and compiz starts I get a wonderful screen of nothing but white with the mouse pointer on top. I can still use the console and recover the system but I haven't worked out which step I forgot to follow when installing the driver manually.

BTW the document I follow is the one linked to from the ATI driver download page
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Don't worry I am a computer technician I can fix it :( it just takes me time :mad:

to adamb23:
I have not replicated your error yet can you post the output of the following command
```

cat /var/log/Xorg.0.log | grep \(EE\)
```

That just shows me any errors when X starts on your machine. If that only produces a few lines also add the output of
```

cat /var/log/Xorg.0.log | grep \(WW\)
```

That will show warnings that the X Server writes when it starts.

---

