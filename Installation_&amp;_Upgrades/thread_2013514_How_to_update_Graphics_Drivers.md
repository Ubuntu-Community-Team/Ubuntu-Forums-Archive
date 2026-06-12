---
title: "How to update Graphics Drivers?"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by danieldiazdon on 2012-06-30
I feel that if I updated my graphics drivers, then my system would run games more smoothly. However, I am unsure of what graphics cards I have and how to update any drivers on Ubuntu. Can someone please explain how to update them? Thanks :D

---

### Post by QIII on 2012-07-01
What card are you using?

You are operating right now on an open source driver if you have not installed a proprietary one.  You need not update anything if the card is working well enough for your needs.

To know how to proceed, we need to know what card you have if you want to install a proprietary driver.

---

### Post by danieldiazdon on 2012-07-01
> **QIII said:**
> What card are you using?

You are operating right now on an open source driver if you have not installed a proprietary one.  You need not update anything if the card is working well enough for your needs.

To know how to proceed, we need to know what card you have if you want to install a proprietary driver.

I honestly, am unsure of what graphics card I am using. Is there a way too see which one im using?

---

### Post by ubudog on 2012-07-01
> **danieldiazdon said:**
> I honestly, am unsure of what graphics card I am using. Is there a way too see which one im using?

Try this:
```
sudo apt-get install mesa-utils
```

Then post the output of:
```
sudo glxinfo
```

inside of # brackets.

---

### Post by danieldiazdon on 2012-07-01
> **ubudog said:**
> Try this:
```
sudo apt-get install mesa-utils
```Then post the output of:
```
sudo glxinfo
```inside of # brackets.
 
I installed it and ran the code and got this:

```
daniel@AdminMan:~$ sudo apt-get install mesa-utils
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.3 kB of archives.
After this operation, 152 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe mesa-utils amd64 8.0.1+git20110129+d8f7d6b-0ubuntu2 [30.3 kB]
Fetched 30.3 kB in 0s (32.1 kB/s)   
Selecting previously unselected package mesa-utils.
(Reading database ... 140746 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
daniel@AdminMan:~$ sudo glx-info
sudo: glx-info: command not found

```

---

### Post by Shadius on 2012-07-01
> **danieldiazdon said:**
> I honestly, am unsure of what graphics card I am using. Is there a way too see which one im using?

Run this code in Terminal:
```
lspci -nnk | grep VGA
```

Or you can go to your *System Settings*, under the **System** heading select **Details**, then from the **Overview**, you'll see your **Graphics**. You can post a screenshot of this, if you like.

---

### Post by ubudog on 2012-07-01
Sorry, remove the dash from glx-info.  +1 to Shadius.

---

### Post by Shadius on 2012-07-01
> **danieldiazdon said:**
> I installed it and ran the code and got this:

```
daniel@AdminMan:~$ sudo apt-get install mesa-utils
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.3 kB of archives.
After this operation, 152 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe mesa-utils amd64 8.0.1+git20110129+d8f7d6b-0ubuntu2 [30.3 kB]
Fetched 30.3 kB in 0s (32.1 kB/s)   
Selecting previously unselected package mesa-utils.
(Reading database ... 140746 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
daniel@AdminMan:~$ sudo glx-info
sudo: glx-info: command not found

```
The command is:
```
sudo glxinfo
``` [COLOR="Red"]not[/COLOR] glx-info

---

### Post by danieldiazdon on 2012-07-01
> **Shadius said:**
> Run this code in Terminal:
```
lspci -nnk | grep VGA
```Or you can go to your *System Settings*, under the **System** heading select **Details**, then from the **Overview**, you'll see your **Graphics**. You can post a screenshot of this, if you like.

I put the code and got this: 
```

daniel@AdminMan:~$ lspci -nnk | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
daniel@AdminMan:~$ 

```

Then this is a picture of going to SYSTEM-DETAILS-GRAPHICS: 

[IMG]http://s17.postimage.org/rov8hdegf/Screenshot_from_2012_07_01_00_17_36.png[/IMG]

---

### Post by Shadius on 2012-07-01
> **ubudog said:**
> +1 to Shadius.

Thank you. :) 

> **ubudog said:**
> Try this:
```
sudo apt-get install mesa-utils
```

Then post the output of:
```
sudo glxinfo
```

inside of # brackets.

Could you tell me what these do? I've never used or seen this before so I'm curious and I do like to learn! :D Plus, I think it'd benefit the original poster to know what those commands do.

---

### Post by danieldiazdon on 2012-07-01
> **Shadius said:**
> The command is:
```
sudo glxinfo
``` [COLOR=Red]not[/COLOR] glx-info

That command gave me the following: 

```
daniel@AdminMan:~$ sudo glxinfo
[sudo] password for daniel: 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, 
    GL_OES_EGL_image, GL_MESA_texture_array, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

daniel@AdminMan:~$ 

```

---

### Post by ubudog on 2012-07-01
> **Shadius said:**
> 
Could you tell me what these do? I've never used or seen this before so I'm curious and I do like to learn! :D Plus, I think it'd benefit the original poster to know what those commands do.

glxinfo comes in the package mesa-utils, so we install that first.  glxinfo is a tool to view information about the OpenGL and GLX implementations running on the X server.  It also shows the graphics card information, which is why I asked the OP to run it.  :) 

My output:
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: VirtualGL
server glx version string: 1.4
server glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SUN_get_transparent_index, GLX_ARB_create_context
client glx vendor string: VirtualGL
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SUN_get_transparent_index, GLX_ARB_create_context
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SUN_get_transparent_index, GLX_ARB_create_context
[B]OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 610M/PCIe/SSE2
OpenGL version string: 4.2.0 NVIDIA 295.40
OpenGL shading language version string: 4.20 NVIDIA via Cg compiler
[/B]OpenGL extensions:
    GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_compatibility, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_indirect, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_ES2_compatibility, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sample_shading, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_atomic_counters, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_image_load_store, 
    GL_ARB_shader_objects, GL_ARB_shader_precision, GL_ARB_shader_subroutine, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_include, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_storage, GL_ARB_texture_swizzle, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_storage, 
    GL_EXT_texture_swizzle, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_timer_query, GL_EXT_transform_feedback2, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_EXT_x11_sync_object, GL_EXT_import_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_alpha_test, 
    GL_NV_blend_minmax, GL_NV_blend_square, GL_NV_complex_primitives, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fbo_color_attachments, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragdepth, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_gpu_program4_1, GL_NV_gpu_program5, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp, 
    GL_NV_texture_multisample, GL_NV_texture_rectangle, GL_NV_texture_shader, 
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, 
    GL_OES_standard_derivatives, GL_OES_texture_3D, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

16 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x092 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x093 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x094 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x096 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09a 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x061 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None

167 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x075 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x076 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x079 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x07a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x07c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x07d 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x07e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x080 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x081 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x082 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x084 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x085 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x086 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x088 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x089 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x08a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x08c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x08e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x090 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x091 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x092 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x095 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x096 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x098 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x09a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x09c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x09e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0a0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0a2 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0a4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0a6 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0a8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0aa 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0ac 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0ad 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0af 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0b0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0b1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0b3 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0b4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0b5 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b7 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0bc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0bd 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0be 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0c2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0c3 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0c4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0c5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0c9 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 Ncon
0x0ca 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 Ncon
0x0cb 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0cc 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0cd 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0ce 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0cf 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d0 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d1 24 tc  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 Ncon
0x0d2 24 tc  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0d3 24 tc  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0d4 32 tc  0  32  0 r  . .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d5 24 tc  0  32  0 r  . .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d6 32 tc  0  32  0 r  y .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d7 24 tc  0  32  0 r  y .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d8 32 tc  0  32  0 r  . .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0d9 24 tc  0  32  0 r  . .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0da 32 tc  0  32  0 r  y .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0db 24 tc  0  32  0 r  y .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0dc 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0dd 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0de 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0df 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0e0 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0e1 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0e2 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0e3 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x0e4 32 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0e5 24 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0e6 32 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0e7 24 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0e8 32 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0e9 24 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0ea 32 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0eb 24 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0ec 32 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0ed 24 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0ee 32 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0ef 24 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0f0 32 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0f1 24 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0f2 32 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0f3 24 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0f4 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0f5 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0f6 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0f7 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0f8 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0f9 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0fa 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0fb 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x0fc 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0fd 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0fe 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x0ff 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x100 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x101 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x102 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x103 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x104 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x105 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x106 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x107 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x108 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x109 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x10a 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x10b 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x10c 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x10d 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x10e 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x10f 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x110 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x111 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x112 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x113 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x114 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x115 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x116 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x117 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x118 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x119 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x11a 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x11b 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon


```

---

### Post by danieldiazdon on 2012-07-01
So were do I go from here? Should I update my graphics driver, if so then how? Thanks :D

---

### Post by Shadius on 2012-07-01
> **danieldiazdon said:**
> That command gave me the following: 

```
daniel@AdminMan:~$ sudo glxinfo
[sudo] password for daniel: 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
[B]OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20[/B]
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, 
    GL_OES_EGL_image, GL_MESA_texture_array, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

daniel@AdminMan:~$ 

```

From ubudog's explanation , yours would be what I've made in bold font and also I've put it below. Thank you ubudog for providing the explanation of the code. :) 

> OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20

---

### Post by danieldiazdon on 2012-07-01
> From ubudog's explanation , yours would be what I've made in bold font  and also I've put it below. Thank you ubudog for providing the  explanation of the code. :smile: 

 	Quote:
 	 	 		 			 				OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20 			 		

Okay, thanks for clarifying that, there was alotta output from that code. Rather crazy. But like I said, I have no idea what this stuff means or whether or not I should update it. Will updating it be beneficial? How would I do so? Thanks GUYS :D

---

### Post by ubudog on 2012-07-01
If everything is working for you, I'd say don't bother with it.

Latest Intel drivers should come by default with Ubuntu (someone correct me if I'm wrong).

You can check in "Additional Drivers" for anything, if you want, but normally Ubuntu would prompt you with "additional drivers are available" if there was anything available.

---

### Post by danieldiazdon on 2012-07-01
> **ubudog said:**
> If everything is working for you, I'd say don't bother with it.

Latest Intel drivers should come by default with Ubuntu (someone correct me if I'm wrong).

You can check in "Additional Drivers" for anything, if you want, but normally Ubuntu would prompt you with "additional drivers are available" if there was anything available.

Alrighty then guys, thanks a ton. I really appreciate all of your help :D

---

### Post by mucklas on 2012-07-01
Hello, I'm butting in here (someone tell me off if I shouldn't) because I *need* to update my driver, even though everything seems to work just fine. I got Diablo 3 for my birthday (yay!) and managed to install it using PlayOnLinux. BUT the game won't run, tells me my graphics driver is out of date.
According to the little plastic sticker on my laptop I've an Intel Core i5-480M processor and the grapics card is just presented as Intel Hd Graphics. I don't know if that helps any. I run 11.10.

I kept the pre-installed windows, just repartitioned it when I installed ubuntu, and on my windows boot I was able to install and run the game after updating the driver. I would prefer to run it in ubuntu, though.

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> Hello, I'm butting in here (someone tell me off if I shouldn't) because I *need* to update my driver, even though everything seems to work just fine. I got Diablo 3 for my birthday (yay!) and managed to install it using PlayOnLinux. BUT the game won't run, tells me my graphics driver is out of date.
According to the little plastic sticker on my laptop I've an Intel Core i5-480M processor and the grapics card is just presented as Intel Hd Graphics. I don't know if that helps any. I run 11.10.

I kept the pre-installed windows, just repartitioned it when I installed ubuntu, and on my windows boot I was able to install and run the game after updating the driver. I would prefer to run it in ubuntu, though.

Since this thread was marked as solved, create a thread of your own, and post back the link here so we can follow it and be able to help you. I'll try to help as best as I can. :)

---

### Post by mucklas on 2012-07-01
Ok :)
Here: [http://ubuntuforums.org/showthread.php?p=12066405#post12066405]("http://ubuntuforums.org/showthread.php?p=12066405#post12066405")

---

