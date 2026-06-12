---
title: "Compiz/glxgears uses indirect rendering on Intel GM965"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by miriad on 2008-09-03
On Latest Intrepid (Fresh install of Alpha 4, updated to current), Compiz defaults to Indirect rendering, and glxgears is incredibly slow (Also indirect rendering I assume). I have textured video (Video on faces of cube), which isnt available with Intel hardware rendering.


Output of glxinfo:

```
name of display: :0.0
Failed to initialize TTM buffer manager.  Falling back to classic.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x56  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x57  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x58  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x59  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5a  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x67  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x69  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6a  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x70  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x73  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x75  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x78  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


```



Output of compiz --replace:

```

me@me-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```


Output of glxgears --info:

```

me@me-laptop:~$ glxgears -info
Failed to initialize TTM buffer manager.  Falling back to classic.
GL_RENDERER   = Mesa DRI Intel(R) 965GM 20061102 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.1
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_separate_stencil GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
297 frames in 5.0 seconds = 59.393 FPS
314 frames in 5.0 seconds = 62.633 FPS
314 frames in 5.0 seconds = 62.635 FPS
290 frames in 5.0 seconds = 57.848 FPS
314 frames in 5.0 seconds = 62.633 FPS
307 frames in 5.0 seconds = 61.239 FPS

```

This is horribly slow, but doesnt show any reason it should be going to indirect rendering.

Anyone got any ideas?

---

### Post by RAOF on 2008-09-03
For compiz, it uses indirect rendering because none of the free drivers support texture_from_pixmap with direct rendering.  This isn't *quite* true, but none of the released drivers do - you need DRI2, which means git snapshots of various pieces of the 3d stack.

For glxgears, nothing suggests to me that it *is* using indirect rendering.

Is general 3d (compiz, other stuff) slow?  If not, there's nothing wrong.

You, like so many, are probably a bit confused about what "indirect vs direct rendering" means.  It's got nothing to do with 3d acceleration - in fact, with mesa 7.1 the *software renderer* supports direct rendering*.  Indirect vs direct is all to do with how programs interact with libGL - "indirect rendering" means the program submits GL commands through X which then submits them to libGL, "direct rendering" means that the program submits GL commands straight to libGL.

* So, people who use "glxinfo | grep direct" to determine whether your drivers are working or not, take note.  It no longer works :).

---

### Post by miriad on 2008-09-03
I think the better question, given that software rendering and Indirect rendering are no longer associated, is:

Why under hardy does glxgears run at ~1700 FPS, and compiz/video rendering/flash games/OpenGL games run smooth, while in Intrepid, I get ~60 FPS, slow/choppy compiz animations/videos, and laggy flash/OpenGL games?

I'd assume this would be caused by software rendering, and if so, is it a regression?

---

### Post by RAOF on 2008-09-04
So all 3d runs slowly.  Yes, that would be a problem.

Your glxinfo data seems fine.  I'd suggest filing a bug (or searching for existing bugs) against the intel driver, attaching the output of glxinfo, dmesg, /var/log/Xorg.0.log, and /etc/X11/xorg.conf.

---

### Post by ntetreau on 2008-09-04
Same intel G965 here, and same low framerate or whatever it's called around 65fps using glxgears.  Compiz seems fine and smooth though, not sure about this issue.  I'll confirm your bug report when it's up.

---

### Post by MattiViljanen on 2008-09-05
I'm having the same situation here, Acer AS2920, Intel G965. Alpha4 -> current, just "rolled over".

Compiz works OK, though.

---

### Post by Josh04 on 2008-09-05
Don't know if it's relevant, but the auto-detect in X has never been able to correctly pick the intel driver for my 965 unless I put the right lines in xorg.conf, and extremely slow 3D could be a result of using the vesa driver.

---

### Post by Jim March on 2008-09-08
Josh, what does your xorg.conf look like?

---

### Post by dixon on 2008-09-08
The same problem here. Just tried the alpha5 LiveCD and glxgears gives me like 60FPS....

HP 6720s with X3100...

---

### Post by Jim March on 2008-09-08
> jim@critter:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


Compiz won't even start up.  Just upgraded fron Hardy yesterday.  Video is Intel 965 on a Dell 1525 lappy (Intel CPU).

---

### Post by xerosis on 2008-09-08
> **Jim March said:**
> Compiz won't even start up.  Just upgraded fron Hardy yesterday.  Video is Intel 965 on a Dell 1525 lappy (Intel CPU).

This is what I get. Does running 'glxinfo' result in a segfault? If so you might be hitting this: [https://bugs.edge.launchpad.net/ubuntu/+source/mesa-utils/+bug/256021](https://bugs.edge.launchpad.net/ubuntu/+source/mesa-utils/+bug/256021)

---

### Post by Josh04 on 2008-09-08
> **Jim March said:**
> Josh, what does your xorg.conf look like?

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "AccelMethod"           "EXA"
        Option          "ExaNoComposite"        "false"
        Option          "MigrationHeuristic"    "greedy"
EndSection

```

Like this, although the last three were performance tweaks for compiz in hardy which I simply copied over, I'm not sure if they're relevant anymore, so I'd try without them.

---

### Post by raggari on 2008-09-08
> **Josh04 said:**
> ```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "AccelMethod"           "EXA"
        Option          "ExaNoComposite"        "false"
        Option          "MigrationHeuristic"    "greedy"
EndSection

```

Like this, although the last three were performance tweaks for compiz in hardy which I simply copied over, I'm not sure if they're relevant anymore, so I'd try without them.

I'm pretty sure that MigrationHeuristic greedy patch was removed because that was useless and causes segfaults.

---

### Post by lefthand on 2008-09-08
> **Jim March said:**
> Compiz won't even start up.  Just upgraded fron Hardy yesterday.  Video is Intel 965 on a Dell 1525 lappy (Intel CPU).

I had the same problem after I upgraded. I found I had to nvidia glx drivers installed that were causing conflicts. Once I got rid of them compiz would start. Still getting low frame rates, but it runs smooth enough.

Update:
Bug report is here: [https://bugs.launchpad.net/ubuntu/+bug/268006](https://bugs.launchpad.net/ubuntu/+bug/268006)

---

### Post by Jim March on 2008-09-09
OK, using Synaptic to systematically nuke NVidia stuff has given my i965 3D again.  I have very basic Compiz running on a two-pane "cube" (flat plane, really) and GLXGears reports about 58fps.

Bit of an improvement anyhow.

This has also repaired by VirtualBox/XP install - it was suffering screen freeze every few seconds.

---

### Post by lefthand on 2008-09-16
It appears as though this has been fixed now. I'm getting 650fps with glxgears now. Everything seems smooth as butter.

---

### Post by miriad on 2008-09-16
This does seem to be fixed. Compiz is much faster now, 700+ in glxgears with compiz enabled.

---

### Post by stats on 2008-10-06
I get 600~ fps in glxgears, however with compiz on the overlay flickers comtinuously. 
glxinfo gives 
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2

video playback is still choppy and uses cpu even though mplayer is set to use xv. I have textured video, which was not possible in hardy, which gives me the feeling the video isnt hardware accelerated

Edit: this is on intel gma 965 (x3100)

---

### Post by heller_barde on 2008-10-22
sorry to bring this up again. first off, i confess not to have ubuntu (i use archlinux) and i never got any decent performance with my GM965... it seems as if it was possible to have decent performance though... i get 60 fps in glxgears as you guys did. could you tell me which versions of which packages you use now that it works?

cheers Heller_Barde

---

### Post by zoomy942 on 2008-10-22
this is all so odd.  I have the same chip and i get 550fps....

---

### Post by Jim March on 2008-10-22
Heller_Barde:

My 965 card is pulling about 600fps in GLXGears right now, being driven by xorg 7.4 series and the "xserver-xorg-video-intel" driver based on the X.org xf86-video-intel driver module.

Now here's the bad news: the "version" is listed as "2:2.4.1-1ubuntu10".

"ubuntu10" means it's the 10th tweak the Ubuntu people have put on it.  That's a lot of tweaking.  Before this latest tweak I was pulling around 275 in GLXGears, prior to the tweak before that I was doing about 550.  So they're messing bigtime with performance-related issues.

That kind of tuning and tweaking doesn't happen with Arch.  You're supposed to do it yourself.  If you're not capable of doing that, and God knows I ain't, then you need to consider Ubuntu, or Fedora, or OpenSUSE or whatever.

Sorry to be blunt...sigh.

---

### Post by heller_barde on 2008-10-23
> **zoomy942 said:**
> this is all so odd.  I have the same chip and i get 550fps....

i have basically the same laptop as you do: 2510p (just without the tablet. the hardware inside is practically the same...) can you please send me your xorg.conf?

---

### Post by heller_barde on 2008-10-23
> **Jim March said:**
> Heller_Barde:

My 965 card is pulling about 600fps in GLXGears right now, being driven by xorg 7.4 series and the "xserver-xorg-video-intel" driver based on the X.org xf86-video-intel driver module.

Now here's the bad news: the "version" is listed as "2:2.4.1-1ubuntu10".

"ubuntu10" means it's the 10th tweak the Ubuntu people have put on it.  That's a lot of tweaking.  Before this latest tweak I was pulling around 275 in GLXGears, prior to the tweak before that I was doing about 550.  So they're messing bigtime with performance-related issues.

That kind of tuning and tweaking doesn't happen with Arch.  You're supposed to do it yourself.  If you're not capable of doing that, and God knows I ain't, then you need to consider Ubuntu, or Fedora, or OpenSUSE or whatever.

Sorry to be blunt...sigh.

I know that perfectly well, and i am capable of doing such tweaks if i know where to put the chisel and where to get the hammer ;) so thanks for the information. now i can start looking for solutions :) 
thank you jim march

PS: sorry for doublepost :(

---

### Post by Jim March on 2008-10-23
Mine:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1280 1400
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


The "Virtual" thing is because I often run two monitors...I don't think it's creating a performance difference.

Sorry about over-explaining, I just wanted to made sure you realized you can't graft Ubuntu pieces straight into Arch :(.

---

### Post by RAOF on 2008-10-23
> **Jim March said:**
> ...
"ubuntu10" means it's the 10th tweak the Ubuntu people have put on it.  That's a lot of tweaking.  Before this latest tweak I was pulling around 275 in GLXGears, prior to the tweak before that I was doing about 550.  So they're messing bigtime with performance-related issues.
...

It's worth noting (yet again) that glxgears is approximately useless as a performance benchmark.  You can have orders of magnitude change in that number with no appreciable real-world performance difference, and driver changes can increase glxgears FPS while *decreasing* real-world performance.

Browsing through the changelog, each of the Ubuntu revisions (with the exception of one no-change rebuild) has been pulling in one or more upstream patches to fix various bugs - none of which has been for performance.

---

### Post by heller_barde on 2008-10-23
> **RAOF said:**
> It's worth noting (yet again) that glxgears is approximately useless as a performance benchmark.  You can have orders of magnitude change in that number with no appreciable real-world performance difference, and driver changes can increase glxgears FPS while *decreasing* real-world performance.

Browsing through the changelog, each of the Ubuntu revisions (with the exception of one no-change rebuild) has been pulling in one or more upstream patches to fix various bugs - none of which has been for performance.

that's true. but i had almost decent performance in compiz a while back. now i have only 8 fps and it's absolutely unusable... so i thought I'd search the interwobs for intel 965GM. unfortunately glxgears is by now established as the poor man's benchmark...

cheers Barde

PS: I'll report back with my success stories...

---

### Post by Panos on 2008-10-23
Thanks for the detailed explanation. I was a littled confused before reading your message because I had the impression that "indirect" meant no true hardware acceleration. However, compiz runs fine with a tone of effects enabled, HD video plays very smooth, and generally Intrepid seems very responsive (I am running the beta with all recent updates on a Dell XPS 1330 laptop with intel 965 graphics card).



> **RAOF said:**
> For compiz, it uses indirect rendering because none of the free drivers support texture_from_pixmap with direct rendering.  This isn't *quite* true, but none of the released drivers do - you need DRI2, which means git snapshots of various pieces of the 3d stack.

For glxgears, nothing suggests to me that it *is* using indirect rendering.

Is general 3d (compiz, other stuff) slow?  If not, there's nothing wrong.

You, like so many, are probably a bit confused about what "indirect vs direct rendering" means.  It's got nothing to do with 3d acceleration - in fact, with mesa 7.1 the *software renderer* supports direct rendering*.  Indirect vs direct is all to do with how programs interact with libGL - "indirect rendering" means the program submits GL commands through X which then submits them to libGL, "direct rendering" means that the program submits GL commands straight to libGL.

* So, people who use "glxinfo | grep direct" to determine whether your drivers are working or not, take note.  It no longer works :).

---

### Post by zoomy942 on 2008-10-23
> **heller_barde said:**
> i have basically the same laptop as you do: 2510p (just without the tablet. the hardware inside is practically the same...) can you please send me your xorg.conf?

sure!!


```
 # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "AccelMethod"           "EXA"
        Option          "ExaNoComposite"        "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option	"Mode"		"Absolute"
EndSection


Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Default Screen" 0 0
        InputDevice    "stylus" "SendCoreEvents"    # Add these three lines
        InputDevice    "eraser" "SendCoreEvents"
	InputDevice	"Cursor" "SendCoreEvents"
EndSection
```

---

### Post by jerrylamos on 2008-10-23
You Tube flashplayer Intrepid is running fine on this IBM Thinkpad R31 1 gHz.  The R31 won't even boot with compiz active.  See bug 277344.

After an Intrepid install I do:
Boot in rescue mode
select Root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

Then Intrepid flashplayer 10.0 r12 runs fine on You Tube, example Leona Lewis.  Oh, yes, full screen Firefox.

Jerry

---

### Post by heller_barde on 2008-10-23
> **zoomy942 said:**
> sure!!

thank you. didn't work. 
i also tried the ubuntu patches for the intel-graphics driver thingie. didn't work (didn't expect it to work) i'll try and recompile the xserver and mesa library tonight with ubuntu patches. lets see, shall we :)

cheers Barde

---

