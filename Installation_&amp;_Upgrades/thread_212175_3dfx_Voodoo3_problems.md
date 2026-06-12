---
title: "3dfx Voodoo3 problems"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by domstyledesign on 2006-07-09
I can't get hardware acceleration working on this 3dfx voodoo3

i've changed the xorg.conf file to only have 16bit depth @ 1024x768 and lower

i've also installed libglide3 and libgl1-mesa-glide3.

here's my glxinfo output:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 6.2.1
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap,
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_SGI_video_sync, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 6.2.1
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap,
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_SGI_video_sync, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap,
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_SGI_video_sync, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 1.5 Mesa 6.2.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_HP_occlusion_test,
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap,
    GL_SGIS_pixel_texture, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_pixel_texture, GL_SGIX_shadow, GL_SGIX_shadow_ambient,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x2c 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x2d 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x30 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x31 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x33 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x34 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x35 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x36 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x37 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x38 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x39 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x3a 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x3c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x3f 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x40 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16 16  0 0 None
```

i found a thread about enabling bus mastering for dri, but it didn't work.

any suggestions?

---

### Post by domstyledesign on 2006-07-09
not sure if this will help, but here's what i get when i try to run enemy territory:
```
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/will/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
gd error (glide): gd error (glide): grSstSelect:  non-existent SSTReceived signal 11, exiting...
```

---

### Post by Leibniz on 2006-07-09
I'm having a similar problem. I was able to get "direct rendering" ubuntu 6.06, just installing libglide3, but every time i try to run anything more interesting than glxgears it crashes(i am also able to run armagetron, but it crashes after one match). I always get a "segmentation fault" o "signal 11, exiting" message, 
This is my glxinfo:
```

manuel@200-127-61-17:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI 20040719 Voodoo3
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_texture_env_add,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_func_separate, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_HP_occlusion_test,
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_window_pos, GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_OES_read_format, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x2c 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 Slow
0x2d 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x33 16 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x34 16 dc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 Slow
0x35 16 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x36 16 dc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x37 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x38 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x39 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x3a 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x3c 16 dc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 Slow
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x3f 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x40 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
manuel@200-127-61-17:~$

```
And this is my xorg.conf
```

manuel@200-127-61-17:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "3Dfx Interactive, Inc. Voodoo 3"
        Driver          "tdfx"
        BusID           "PCI:1:0:0"
        VideoRam        16384
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-55
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "3Dfx Interactive, Inc. Voodoo 3"
        Monitor         "SyncMaster"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection

EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
manuel@200-127-61-17:~$

```

I was able to use it normally on Slackware and Debian Sarge, but on all the others I tried(Debian Etch, sid and Ubuntu dapper), it crashed.

Hope someone knows how to fix this, there aren't many 3dfx users out there

BTW: Hi ubuntuforums ^_^
BTW2: Sorry for mi awful english :oops: I'm Argentine.

---

### Post by Max Luebbe on 2006-07-09
First of all, your english is nothing to be ashamed of! You need to give yourself more credit than you are doing, it's fine.

Interesting problem, nothing stands out to me from those files. I'll get my v3 3000 out later tonight when I'm putting together an old machine, and see if I can get it working.

---

### Post by domstyledesign on 2006-07-10
*bump*

anyone?  would i have better luck asking in a different forum?

---

### Post by Leibniz on 2006-07-10
> **domstyledesign said:**
> *bump*

anyone?  would i have better luck asking in a different forum?
I think i found your problem, you should install libgl1-mesa-dri instead of libgl1-mesa-glide3 , it's the only way to get direct rendering(it uses glide as a HAL for glx), maybe you'll be lucky and it won't crash(like it's happening to me T_T).

---

### Post by domstyledesign on 2006-07-10
> **Leibniz said:**
> I think i found your problem, you should install libgl1-mesa-dri instead of libgl1-mesa-glide3 , it's the only way to get direct rendering(it uses glide as a HAL for glx), maybe you'll be lucky and it won't crash(like it's happening to me T_T).

did that, et still crashes (later than before) and now i get these messages from glxinfo:
```
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
```

---

### Post by Leibniz on 2006-07-10
> **domstyledesign said:**
> did that, et still crashes (later than before) and now i get these messages from glxinfo:
```
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
```

It means you have direct rendering :) (see glxinfo), but it always crashes somewhere T_T . I don't know where is the problem, but it always crashes with a "segmentation fault" or a "SDL parachute deployed" message :(. Now we're stuck in the same place.

---

### Post by Leibniz on 2006-07-11
I don't even know what caused this, but it is fixed. I was trying to get xgl to work(don't laugh at me), so i added this line to sources.list:
```

deb http://ubuntu.compiz.net/ dapper main aiglx

```
In that repo were the patches i needed, but i don't know wich ones(T_T), i just saw that a few dri packages were newer and did "apt-get upgrade", and restarted the X server, that seemed to fix it af(for me). Now i'll never know what caused it :( , i'll be to busy playing.

---

### Post by glenduncanscott on 2006-10-28
> Hope someone knows how to fix this, there aren't many 3DFX users out there

Yep Leibniz there sure are other 3DFX users out there :D

I'm not too sure either whether it's possible to ever get 3D acceleration working with this type of card.

Currently I'm only able to load the "vesa" driver as the "tdfx" produces a black screen on startup (Kubuntu Edgy Eft NOT Dapper Drake), with a frozen mouse pointer in the center of the screen! Great.

I've searched the forums and spent the day experimenting with /etc/X11/xorg.conf trying to get things to work but to no avail. Could someone have a look this file and see if anything is missing or outta place. Would be most grateful for any suggestions:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load	"bitmap"
	Load	"dri"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:1:5:0"
        Option          "UseFBDev"       "true"
EndSection

Section "Monitor"
	Identifier	"DELL D1025HE"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"DELL D1025HE"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by lig1uk on 2006-10-30
I am in the same position. I have been trying desperately to get the Ubuntu 6.10 live disk working.
I also have the Voodoo3 card .. and all I get is a completely blank screen and a locck up of the mouse.
Looking through these forums nothing that I have seen will work. I have tried all kinds of things including pressing Ctrl-Alt-F1 and Ctl-Alt-Backspace but nothing helps. I can't get to see anything on the screen other some garbled lines. 
It is very frustrating.
I really wanted to use Ubuntu. Knoppix works just fine with the xorg-tdfx file. What do I need to do with Edgy Eft?? Is it a bug??

---

### Post by glenduncanscott on 2006-10-30
You sound like you've had more problems than me, I was able to get into the live CD ok. It was after the install/reboot that I got a blank screen if I tried to load the "tdfx" driver. Have you tried running safe graphics mode? Or tried CTRL+ALT+F1 (at black screen) to get to the command line then accessing ```
sudo dpkg-reconfigure xserver-xorg
``` or ```
sudo nano /etc/X11/xorg.conf
``` file so that you could change the "tdfx" to "vesa" driver, which should get you up and running. Might have to ask an expert whether this last option is possible to do with the Live CD.

Currently reverted back to Kubuntu 6.06 for the time being until Edgy problems get resolved. Although there is still a bug with 3D acceleration read more here:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-tdfx/+bug/44112](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-tdfx/+bug/44112)

It appears possible, will have to tinker some more, hope you have some better success.

---

### Post by lig1uk on 2006-10-31
Thanks for the comprehensive reply glenduncanscott. But whatever options that I try with Edgy nothing is visable on the display and it locks up.
I have tried the Dapper Drake and it works.. but Edgy doesn't with this setup.
I assume there is a bug therefore. It certainly is a backward step..

---

### Post by kingcharles1666 on 2006-10-31
Hi there,

just to let you know that I have wrestled with the same issue and have reverted back to 6.06 also. I did manage to get it up to the login screen with the tdfx driver. But when logging into my or any other profile the system would log me out after a few seconds. And that time (# of secs) would vary. I can remember that the .xsession-errors in my home directory had some strange messages but I cannot remember them and I did not save a copy. (they have been overwritten by now) The message was something like "connection lost to screen" or "application lost connection to screen"
Anyway I gave up not knowing that there were more users out there.
I hope that somebody can shed some light on this problem because I would like to be able to use the voodoo card for some more time.

Charles

---

### Post by darkteckno on 2006-11-09
I'm getting the same problem with Xubuntu aswell

---

### Post by darkteckno on 2006-12-16
bump

---

### Post by valnar on 2007-01-30
Anybody try a Voodoo 3000 with Feisty yet?  Did they fix it or regress further into the abyss?

---

### Post by MadMarv on 2007-02-07
Hi guys, I also had xserver problems after upgrading to Edgy. I was able to eventually get things up, using the the vesa driver at 1024X768X16 without using videoram, framebuffer or composite (I use Xubuntu), but it wasn't stable, Any attempt to run video locked up (Xfmedia) or ended the session (gXine.) I played with it for awhile, but eventually reinstalled Dapper. Too bad, I really liked Edgy's look, and it was noticeably faster opening most applications.

Wish I could have come up with a solution, but then I'm not sure anyone has-

---

### Post by kingcharles1666 on 2007-02-08
There is a patch, but I have not tried it as I am now back at dapper

[http://ubuntuforums.org/showthread.php?t=301277](http://ubuntuforums.org/showthread.php?t=301277)

Charles

---

### Post by jhansonxi on 2007-04-12
The Feisty beta + updates now works, more or less.  You need to install libglide else any OpenGL app will kill X (Bug #105312).  Just remember that 3D acceleration only works in 16-bit color (DefaultDepth 16 in xorg.conf) at a max resolution of 1024x768.  You don't need to delete 24-bit entries in xorg.conf as some howtos indicate.

I am having problems with Supertux in 16-bit (Bug #106034) but Chromium, Planet Penguin Racer, Blob Wars, Neverball, Armagetron, and rss-glx screensavers all work.  Maybe someone can try Quake.

Initially with the beta I was having problems getting any OpenGL app to run (Bug #94945) but recent updates seem to have fixed the problem.  I did encounter a problem with X not obtaining the DDC/EDID settings for the monitor (Bug #105629).  I had to set HorizSync and VertRefresh manually in the monitor section of xorg.conf.

---

### Post by jhansonxi on 2007-04-16
I just upgraded to the Xubuntu RC candidate 20070415.  There is a substantial improvement in 3D graphics speed.  I retested the games and a few new ones.  Supertux still doesn't work.  Trigger works if you edit ~/.trigger/trigger.conf and set requiredepth="no".  Slune and Trackballs crash.  Supertuxkart is still too slow.  Neverball is playable but some text is missing.  The rest of the bugs are still present.

---

### Post by jhansonxi on 2007-04-18
Slune is segfaulting with a TNT2 M64 also, so it's not 3dfx specific. [Bug #107394](https://bugs.launchpad.net/ubuntu/+source/slune/+bug/107394)

---

