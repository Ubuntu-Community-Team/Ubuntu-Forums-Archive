---
title: "[SOLVED] Gutsy In, ATI Driver OUT???"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by kshane on 2007-10-16
I have put gutsy back on my system.  Upgraded through Synaptic.  All seems to have gone well, but I can't get the mesa driver out and proprietary ATI/fglrx in!

fglrxinfo:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

glxinfo:
```


Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias


```

xorg.conf:
```


Section "Monitor"
	Identifier   "1772ED"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Default Card"
	Monitor    "1772ED"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



Section "Extensions"
	Option "Composite" "Disable"
EndSection

```


Can any one help?  I've searched the forums and I have tried everything I can think of.  I had this problem before, but was unable to repeat with this install.

---

### Post by kshane on 2007-10-16
Well, sorry for taking up board space with this thread.  I fixed my own problem (**AGAIN!**). * I hope this helps others.*

What I did was to follow the instructions in the below link and made changes to **ENVY**.  I had to run ENVY twice, but the second time it worked and I now am running off ATI's driver as opposed to MESA.

[http://albertomilone.com/wordpress/?p=107](http://albertomilone.com/wordpress/?p=107)

I would strongly recommend to anyone with an ATI X**** to use ENVY to put the ATI Proprietary driver in place.  It's sinfully easy and just plain works!

Thanks!

Kevin

---

### Post by undine on 2007-10-16
Thanks :) I tried everything, and this is the only thing that has worked. 

PS: I like the quote in your signature too ;)

---

### Post by kshane on 2007-10-16
> **undine said:**
> Thanks :) I tried everything, and this is the only thing that has worked. 

PS: I like the quote in your signature too ;)

Thanks...  I changed it today, though...  :(

Glad it worked for you!  :)

Kevin

---

