---
title: "HD 3650 mobility on hp 8530p problems!!"
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gtramt1 on 2009-05-15
Hello!

Finally I have installed Karmic in hope that fglrx will work! I have tried installing Proprietary drivers but this didn't work. So I tried [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") 


also problems!! i got errors while installing that i have to build fglrx in dkms tree ...so i did and get error while doing it...problem at Proprietary was fglrx module not found....


I HATE ATI AND I HATE AMD!!!!!

and one more thing why in ubuntu(intrepid, karmic)battery lifetime is ONLY about two hours (in windows it's normally about 4,5 hours)

NEED HELP!!!!

almost forgot
```
gtramt1@GAPI-LT:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
86:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 14)
86:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev bb)
86:09.5 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ff)
```

---

### Post by taavikko on 2009-05-15
If you bothered to read documentation you'ved came to realize that ATI has dropped support for r600 series.
So no support from fglrx AFAIK

radeon driver should work just nice, but no good playing games.

---

### Post by gtramt1 on 2009-05-15
I haven't heard for  ATI Mobility RadeonTM X3650...is x meant also for HD or am I wrong and ATI dropped support for R300-R500 cards, but if i am not wrong I have r600 or more specific r635!

Am I wrong?

---

### Post by alphacrucis2 on 2009-05-15
> **gtramt1 said:**
> I haven't heard for  ATI Mobility RadeonTM X3650...is x meant also for HD or am I wrong and ATI dropped support for R300-R500 cards, but if i am not wrong I have r600 or more specific r635!

Am I wrong?

I'm pretty sure the hd 3650 is still supported by Catalyst 9.4. Check on the ATI site. My laptop with a hd 3400 runs fine with the Catalyst 9.4 fglrx. I couldn't seem to get it to install via the Hardware drivers menu for some reason it failed to download. So I manually installed fglrx via apt-get then activated via the hardware drivers menu. It still wouldn't work until I did

```
sudo aticonfig --initial -f
```

I also vaguely recall though that a few specific non legacy cards were blacklisted because of some problem so you may want to check that out too.

---

### Post by gtramt1 on 2009-05-15
can you bi more specific how did you do it?
:popcorn:
thanks!

and can anybody explain me why my xorg.conf on freshly installed and upgraded karmic is empty? could be that normal?:confused::confused:

---

### Post by alphacrucis2 on 2009-05-15
> **gtramt1 said:**
> can you bi more specific how did you do it?
:popcorn:
thanks!

and can anybody explain me why my xorg.conf on freshly installed and upgraded karmic is empty? could be that normal?:confused::confused:

Going from memory this is what I did with Jaunty for the hd 3400. I haven't tried Karmic on my laptop with the ATI graphics yet.


```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f

```

Then reboot


I recall that between the two commands I did an activate via the Hardware drivers gui though I don't know if that is necessary or not.

---

### Post by DougieFresh4U on 2009-05-15
> **alphacrucis2 said:**
> Going from memory this is what I did with Jaunty for the hd 3400. I haven't tried Karmic on my laptop with the ATI graphics yet.


```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f

```

Then reboot


I recall that between the two commands I did an activate via the Hardware drivers gui though I don't know if that is necessary or not.

Tried that with ATI Radeon HD3200 and got 'black screen of death' with red squiggly line on top  ):P

---

### Post by gzed on 2009-05-15
I haven't yet installed karmic but it apparently has the same problem my jaunty install (with kernel 2.6.30) has:

the fglrx module won't compile due to kernel changes, we'll need to wait for either a new driver release from AMD/ATI that supports this kernel version or write a patch to fix it.

I have the same chip you have, but on a discrete graphic card (Radeon HD3650).

---

### Post by DanaG on 2009-05-15
Hmm, looks like you may be running into this issue:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600)

The workaround that worked for me: sudo aticonfig --acpi-services=off

Oh, and the 9.4 drivers improve OpenGL-within-OpenGL rendering (such as glxgears under compiz).

---

### Post by gtramt1 on 2009-05-17
> **alphacrucis2 said:**
> Going from memory this is what I did with Jaunty for the hd 3400. I haven't tried Karmic on my laptop with the ATI graphics yet.


```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f

```Then reboot


I recall that between the two commands I did an activate via the Hardware drivers gui though I don't know if that is necessary or not.


before reboot i did what you have written and also
 aticonfig --acpi-services=off
and before reboot tryed:

```
gtramt1@GAPI-LT:~$ fglrxinfo && glxinfo
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.4)

name of display: :0.0
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
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
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_swap_barrier, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.4)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xdf 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe0 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe1 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe2 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe3 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xe4 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xe5 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xe6 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xe7 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe8 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe9 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xea 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xeb 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xec 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xed 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xee 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xef 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf0 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf1 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf2 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf3 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xf4 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xf5 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xf6 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xf7 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf8 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf9 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xfa 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xfb 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xfc 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xfd 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xfe 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xff 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x100 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x101 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x102 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x103 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x104 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x105 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x106 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x107 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x108 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x109 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x10a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x10b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x10c 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x10d 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x10e 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x10f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x110 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x111 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x112 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x113 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x114 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x115 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x116 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x117 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x118 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x119 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x11a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x11b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

135 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x5f  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x60  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x61  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x62  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x63  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x64  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x65  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x66  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x67  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x68  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x69  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x6a  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x6b  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x6c  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x6d  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x6e  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x6f  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x70  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x71  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x72  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x73  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x74  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x75  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x76  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x77  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x78  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x79  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x7a  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x7b  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x7c  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x7d  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x7e  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x7f  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x80  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x81  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x82  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x83  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x84  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x85  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x86  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x87  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x88  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x89  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x8a  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x8b  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x8c  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x8d  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x8e  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x8f  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x90  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x91  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x92  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x93  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x94  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x95  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x96  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x97  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x98  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x99  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x9a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x9b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9f  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0xa0  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0xa1  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0xa2  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0xa3  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0xa4  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0xa5  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0xa6  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0xa7  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0xa8  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0xa9  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0xaa  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0xab  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0xac  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0xad  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0xae  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0xaf  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0xb0  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xb1  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0xb2  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xb3  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0xb4  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0xb5  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0xb6  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0xb7  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xb8  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xb9  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xba  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xbb  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0xbc  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0xbd  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0xbe  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0xbf  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc0  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc1  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc2  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc3  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xc4  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xc5  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xc6  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xc7  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xc8  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xc9  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xca  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcb  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xcc  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xcd  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xce  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xcf  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd0  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd1  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd2  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd3  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xd4  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xd5  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xd6  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xd7  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xd8  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xd9  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xda  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xdb  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xdc  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xdd  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xde  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xde  0 dc  0 128  0    y  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Slow
0xde  0 dc  0 128  0    .  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Slow
0xde  0 dc  0 64  0    y  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0xde  0 dc  0 64  0    .  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0xde  0 dc  0 32  0    y  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None
0xde  0 dc  0 32  0    .  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None
0xde  0 dc  0 32  0 r  y  . 10 10 10  2  0 24  0  0  0  0  0  0 0 None

```


i am expecting black screen of dead after reboot!

---

### Post by gtramt1 on 2009-05-18
ok when rebooted black screen yeah!!!

so is there any way to fix it or i have to install ubuntu again!!??;)

---

### Post by alphacrucis2 on 2009-05-19
> **gtramt1 said:**
> ok when rebooted black screen yeah!!!

so is there any way to fix it or i have to install ubuntu again!!??;)

Catalyst 9.5 is about to come out. I guess you could try that when it appears.

---

### Post by gtramt1 on 2009-05-19
ok i've got [www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run]("http://ubuntuforums.org/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run")
tried on karmic no effect because of dkms tree again...
tried on jaunty maybe changed black screen of dead.... 


ati=D>cannonical=D>

---

### Post by alphacrucis2 on 2009-05-20
> **gtramt1 said:**
> ok i've got [www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run]("http://ubuntuforums.org/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run")
tried on karmic no effect because of dkms tree again...
tried on jaunty maybe changed black screen of dead.... 


ati=D>cannonical=D>


I just tried 9.5 catalyst on my Jaunty machine, it is a definite improvement for me. I can now run compiz and googleearth at the same time which I never could before. I can't try on Karmic as my test machine doesn't have an ATI card. Are you sure your particular card isn't blacklisted?

---

### Post by DougieFresh4U on 2009-05-20
> **alphacrucis2 said:**
> I just tried 9.5 catalyst on my Jaunty machine, it is a definite improvement for me. I can now run compiz and googleearth at the same time which I never could before. I can't try on Karmic as my test machine doesn't have an ATI card. Are you sure your particular card isn't blacklisted?

The .28 kernel is fine, but are you using the .30 kernel? I have an onboard 'ATI Radeon HD 3200' and 'fglrx' works great on my Jaunty install with the .28 kernel but have had drama with the .30 on my Karmic install.

---

### Post by plun on 2009-05-20
> **DougieFresh4U said:**
> The .28 kernel is fine, but are you using the .30 kernel? I have an onboard 'ATI Radeon HD 3200' and 'fglrx' works great on my Jaunty install with the .28 kernel but have had drama with the .30 on my Karmic install.

From Phoronix:

> There is also no Linux 2.6.29 kernel support yet, nor any support for the forthcoming Linux 2.6.30 kernel.


[http://www.phoronix.com/scan.php?page=news_item&px=NzI3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NzI3OQ)

---

### Post by markbuntu on 2009-05-20
The Mobility HD3650 is not listed in the relase notes as supported. The Radeon HD3650 is, but they are not the same thing.

---

### Post by TheBeet on 2009-05-21
> **markbuntu said:**
> The Mobility HD3650 is not listed in the relase notes as supported. The Radeon HD3650 is, but they are not the same thing.

I can confirm this. I tried installing 9.5 and got black screened.

---

### Post by MacUntu on 2009-05-22
Hm... about to buy a Lenovo ThinkPad T500 but that doesn't sound promising. :|

---

### Post by gtramt1 on 2009-05-22
so can anyone tell me what do with drivers...go back on intrepid or what...!!?!?
i don't see anything new or better not in jaunty or karmic... i fixed fn keys in intrepid, also graphics works, only battery is not lasting very long...

I really don't know what is happening to ATI or AMD....can anybody tell me distro with better battery time..!!!

thanks guys!!!

---

### Post by gtramt1 on 2009-05-29
Dead or what?!?!?](*,)](*,)=;[-o<:sad:

---

### Post by velozoom on 2009-05-31
> **MacUntu said:**
> Hm... about to buy a Lenovo ThinkPad T500 but that doesn't sound promising. :|

I have a T500 and I can't use anything other than the opensource drivers on my Jaunty install.  No Compiz, no Emerald.  Video seems to work ok but I have some DMA issues I haven't had the time to solve.  

This laptop worked amazingly well on Intrepid.  I'm really considering reverting despite it being a full re-install.  My /home is mounted on a separate partition so all me personal bits are already saved.  

Come on developers, how can we go from a WORKING version to a broken one?!?!?!

---

### Post by MacUntu on 2009-06-01
> **velozoom said:**
> I have a T500 and I can't use anything other than the opensource drivers on my Jaunty install.  No Compiz, no Emerald.  Video seems to work ok but I have some DMA issues I haven't had the time to solve.

Oh dear... I really don't want another Nvidia GPU after their last major manufacturing screw-up (that's why I need to replace an otherwise fully functional notebook), but if THAT's the alternative I really have to think about it. :(

Thanks for your input!

---

### Post by gtramt1 on 2009-06-16
anyone tried [SIZE=5]new[SIZE=3] [/SIZE][/SIZE]catalyst [SIZE=5]9.6?????[/SIZE]](*,)](*,)](*,):-s:-s

---

### Post by bambam_ on 2009-06-17
> **gtramt1 said:**
> anyone tried [SIZE=5]new[SIZE=3] [/SIZE][/SIZE]catalyst [SIZE=5]9.6?????[/SIZE]](*,)](*,)](*,):-s:-s
Jup, just tried with an 8530P and got the nice black screen. Wasn't there something about ATI releasing open source drivers? There might be enough people requesting a working driver with these cards by now :-)

---

### Post by gtramt1 on 2009-08-17
hello....!


so i am using xp and io wonder if ati fixed drivers for koala with 9.7 or is the same ****?

thanks!

---

### Post by laborg on 2009-08-17
> **velozoom said:**
> I have a T500 and I can't use anything other than the opensource drivers on my Jaunty install.  No Compiz, no Emerald.  Video seems to work ok but I have some DMA issues I haven't had the time to solve.  


On my T500 I can decide which graphic card should be used. And using the Intel chip gives me a very nice experience with karmic. You should give it a try as long as you own such a dual graphic card T500...

---

### Post by eL Belga on 2009-09-11
I managed to properly install the proprietary drivers on my HP EliteBook 8530p.

You can find the instructions on my blog: [http://blog.desair-homble.be/#post50](http://blog.desair-homble.be/#post50)

The essential part is this:
> 
First follow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) using the "Installing the drivers manually " section.

_**BUT BEFORE YOU RESTART**_ you also have to run the following command: *sudo **aticonfig --acpi-services=off*

Now you're good to go and you can restart your system. Normally everything should be working fine.


Greetz,
Tom

---

