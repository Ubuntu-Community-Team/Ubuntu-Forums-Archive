---
title: "ATI fglrx driver in Intrepid"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by soxs on 2008-10-20
Hi
I just got the beta up and running and ran straight into the first problem.

I installed the fglrx driver from the repos which was said to be the first one to support xserver 1.5.x and xorg 7.4.x
So installed it and t:he reboot just worked flawlessly and glxinfo and fglrxinfo confimred the correctness of what I did.

But ET:QW refused to render Strog Objects (at least it seemed like that, or it maybe something else alike) at least I got ugly triangles all over the screen when viewing certain areas of a map.
As I had this before, I added some advanced options to my /etc/X11/xorg.conf and updated /etc/ati/amd...conf

I rebooted and got a blackscreen, so.. I am quite stunned as these were the EXACT SAME options as I used in hardy.

I know thtat xserver / xorg are now autdetecting a lot of input/output devices, and xorg.conf will get deprecated within the next 3 years or so (just a guess), but if so, where can I put in my xcustom pimped options which whose etqw worked flawlessly??

Plx help

---

### Post by soxs on 2008-10-21
Any Ideas? Or did nobody even try to run etqw within 8.10 and ubuntus repo fglrx driver (which atm is trhe only ati driver that supports xserver 1.5 / xorg 7.4)

---

### Post by soxs on 2008-10-21
Ok, here we go:
I at least identified one option which makes this whole thing go wacky (you may try it yourself).
Setting ```
Option      "TexturedXRender" "1"
``` to one (as set in that example will end in a one time blink of your loginscreen and then disappearing until the next reboot.
You may add this to your /etc/X11/xorg.conf and update your xorg.conf via this commadn in order to make /etc/ati/amdpcsb accept theses changes.
```
 sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

[COLOR="Red"][B][SIZE="6"]CAUTION NOTE: This will render your system unable to run any userinterface! In order to undo it, you will have to set that option in your xorg.conf to 0 and update /etc/ati/amdpcsb in order to accept theses changes.[/SIZE]
```
 sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```[SIZE="6"] again!
Removing the entry won't help at all![/SIZE][/B][/COLOR]

Edit: ETQW missrendering is still present...

---

### Post by khughitt on 2008-10-24
*Bump*

Anyone able to get fglrx working on ibex?

---

### Post by bash on 2008-10-24
Yea me. Without any problems actually. Just installed it through the "Hardware driver manager" (jockey), as always.

---

### Post by cjazz on 2008-10-24
No problems for me either.

---

### Post by pulpo69 on 2008-10-24
fglrx without problems.

---

### Post by mojo636 on 2008-10-24
Nothing appears in the Hardware driver manager for me. Very frustrating. When i install it from the repos it loads in low graphics mode because it cannot configure my card.

---

### Post by soxs on 2008-10-25
> **mojo636 said:**
> Nothing appears in the Hardware driver manager for me. Very frustrating. When i install it from the repos it loads in low graphics mode because it cannot configure my card.

Same for me using an Radeon HD 4870... I installed the driver via sudo ```
apt-get install xorg-driver-fglrx
``` and got the said problems

ad changed the driver name in /etc/X11/xorg.conf from "vesa" (maybe radeon or radeonhd or ati) to "fglrx"

---

### Post by z0r on 2008-10-25
For me it is visible in the Hardware Drivers, but I can't activate it. When I click Activate it looks like it's doing something (a progress bar comes up), but it remains inactive.

---

### Post by soxs on 2008-10-25
> **z0r said:**
> For me it is visible in the Hardware Drivers, but I can't activate it. When I click Activate it looks like it's doing something (a progress bar comes up), but it remains inactive.
Well, had this aswell on my previous alpha install and it was messed up afterwards and I decided to reinstall it at betastage

---

### Post by rturner on 2008-10-25
I enables fglrx through synaptic and after rebooting it showed up under hardware drivers.  Activated with no problems.

---

### Post by soxs on 2008-10-26
Did anyone of you try to run ET:QW, as I actually have 3D acceleration, but ETQW has serious misrenderings...

---

### Post by khughitt on 2008-10-26
I've been using the Radeon with my Mobility X1600 the last couple of days, and for a while everything was going really well: 3d effects worked from the start and were pretty smooth, no glitches. When I started to use the system more though it started to lock up during certain actions (especially when alt-tabbing or flipping through firefox tabs). After several times of the system freezing up completely (not even shift + backspace would work), I've switched back to metacity. So far things seem more stable now.

I'm considering trying out ATI, but since the latest ATI driver release only supports up to Xorg 7.3, I'm a little hesitant to try it.

---

### Post by raulih on 2008-10-26
> **z0r said:**
> For me it is visible in the Hardware Drivers, but I can't activate it. When I click Activate it looks like it's doing something (a progress bar comes up), but it remains inactive.

I did the upgrade from Hardy, and I'm now having the same behaviour. On boot (nosplash) i get an error message about missing kernel module.

With glxinfo and glxgears i get this:

```
$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
```

---

### Post by raulih on 2008-10-26
I'm not sure what exactly made the trick. I was trying manual install from [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") but it didn't work in the end. After that I reverted the changes from that guide and **reinstalled** in synaptic packages *fglrx-amdcccle*, *fglrx-kernel-source*, *fglrx-modaliases* and *xorg-driver-fglrx* and now everything works. 

May be just the reinstallation was what was needed, but there may have happened something else from the tutorial too...

---

### Post by ktp on 2008-10-26
I have seen reinstalling fix things for people.  It seems to help when you were previously using ATI open source drivers.

---

### Post by raulih on 2008-10-26
> **ktp said:**
> I have seen reinstalling fix things for people.  It seems to help when you were previously using ATI open source drivers.

It was perhaps the reinstall, though I thought I tried that already before, but possibly not to all of the packages.

---

### Post by terrax on 2008-10-27
I installed from Intrepid RC.

At first I couldn't see fglrx in the restricted hardware manager. I then did a manual sudo apt-get install fglrx etc...

After reboot I see an entry in restricted hardware manager, and I could activate it.

After activation and reboot, everything seems to works. Thought I haven't tried any fancy 3d besides glxgears (and it crashed my desktop layout, so I needed to do a ctrl + alt + backspace). When I say crash, it doesn't lockup or anything, but lowerhalf of the screen is shown in the upper half screen??? :D

Besides that everything else seems to work.

---

### Post by inportb on 2008-10-27
While the installation proceeded smoothly and I have a perfectly working fglrx, I think I prefer radeon... and might be switching back when Intrepid hits the street.

---

### Post by SaddaGocaraRupa on 2008-10-28
I used the hardware driver tool to get the fglrx drivers to work in intrepid. It all looks good, but I can't run compiz.

```
gui@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMDX_vertex_shader_tessellator, GL_AMD_performance_monitor, 
    GL_AMD_texture_texture4, GL_ARB_color_buffer_float, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_instanced, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_buffer_float, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

81 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x49 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x71 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x72 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x89 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon

83 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x48  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x49  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x70  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon
0x89  0 tc  0 128  0    y  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon
0x89  0 tc  0 128  0    .  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon

```

If I run compiz-check, i get:
```
gui@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

Any idea why it wouldn't render?

Cheers

edit: did fglrxinfo. result:

> gui@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release


---

### Post by khughitt on 2008-10-28
> Error: No rendering method in use (AIGLX, Xgl or Nvidia)

I think that is probably your problem. Can you post the contents of your /etc/X11/xorg.conf file?

To use AIGLX, I believe you will want to have:

Section "Module"
	Load	"glx"
EndSection

If that doesn't work, you can try XGL. There used to be a package in the repos like "xserver-xorg-xgl," but I don't see it in there anymore. Anyone else know if it's still possible to install xgl on 8.10?

---

### Post by SaddaGocaraRupa on 2008-10-28
> **pwnedd said:**
> I think that is probably your problem. Can you post the contents of your /etc/X11/xorg.conf file?

To use AIGLX, I believe you will want to have:

Section "Module"
	Load	"glx"
EndSection

If that doesn't work, you can try XGL. There used to be a package in the repos like "xserver-xorg-xgl," but I don't see it in there anymore. Anyone else know if it's still possible to install xgl on 8.10?
It's:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```
 I have ```
Section "Module"
	Load	"glx"

```
but I also have 
```
Disable	"dri2"
```

??

---

### Post by bpl07 on 2008-10-28
Here's my relevant info from xorg.conf, it's been working great so far, compiz and everything else:

> Section "Device"

#	Option	    "BackingStore" "on" 		#->Helps alot
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on" 	#->This one IS absolutely NEEDED! It shouldn't be missed!
	Option	    "TexturedVideo" "on" 		#->AVIVO accelerated video through 3D engine ideal for Compiz(speaking for fullscreen always).
	Option	    "VideoOverlay" "off"		#->Set it to "on" only if you use tvtime.
	Option	    "OpenGLOverlay" "off"		#->Deprecated generally that's why off. 
	Option	    "Textured2D" "on" 			#->Experimental now works for all!
	Option	    "TexturedXrender" "off" 		#->Experimental doesn't work for 2D Window Managers with 8.5 Catalyst
	Option	    "UseFastTLS" "1"			#->Enable/disable fast thread local storage.
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
EndSection

Notice I have backingstore turned off.  This is a bug for what appears to be all drivers, here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274988").

> Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

Make sure you have the dri section, this might be why you don't have compiz.

> Section "ServerLayout"
	Identifier     "Default Layout"
	Option	    "AIGLX" "true"
EndSection

---

### Post by sdowney717 on 2008-10-28
This xorg lets compiz run for me

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Device          "Configured Video Device"
	Monitor         "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier      "Default Layout"
	Screen          "Default Screen"
EndSection

Section "Device"
	Identifier      "Configured Video Device"
	Option          "AccelMethod"   "EXA"
	Option          "AccelDFS"      "off"
	Option          "AGPMode"       "4"
	Option          "AGPFastWrite"  "1"
	Option		"EnablePageFlip"
	Option 		"ColorTiling"
	Driver	"fglrx"
EndSection

Section "ServerFlags"
	Option "IgnoreABI" "True"
EndSection


```

---

### Post by bpl07 on 2008-10-28
sdowney717,

fglrx uses xaa, it doesn't support exa yet.  A lot of the options you have set work well for the open source driver but are probably ignored by the proprietary driver.  I would comment these out if I were you:

> 	Option          "AccelMethod"   "EXA"
	Option          "AccelDFS"      "off"
	Option		"EnablePageFlip"
	Option 		"ColorTiling"

If you have an agp card you might as well keep the agp options, but you can check /var/log/Xorg.0.log to see if it's being used or not.

---

### Post by soxs on 2008-10-28
> **SaddaGocaraRupa said:**
> It's:

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Extensions"
    Option        "Composite"    "Enable"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection
``` I have ```
Section "Module"
    Load    "glx"

```but I also have 
```
Disable    "dri2"
```??

Disabling dri2 which is quite new and NOT supported by fglrx driver yet, doesn't mean you don't have dri loaded at all. dri is loaded by default...

---

### Post by SaddaGocaraRupa on 2008-10-30
> **soxs said:**
> Disabling dri2 which is quite new and NOT supported by fglrx driver yet, doesn't mean you don't have dri loaded at all. dri is loaded by default...

OK...do you know what's wrong then?

---

