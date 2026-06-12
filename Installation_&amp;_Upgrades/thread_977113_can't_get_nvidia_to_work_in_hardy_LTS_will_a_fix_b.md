---
title: "can't get nvidia to work in hardy LTS will a fix be available?"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-11-09
Hi! 
I am unable to use any nvidia driver in hardy LTS, and it seems I am not alone!  Even Ibex has problems with nvidia:
It won't work after installing all components in Synaptic, or via envy or changing the screen, monitor and display device settings copied from my  gedit /etc/X11/xorg.conf file in Gutsy to hardy.  At least in Gutsy I could use the generic nvidia Gforce4 driver that installed automatically and also choose it from Screens and Graphics.  

Now I can't find this app. in Synaptic, nor access anything in monitor control app. and I must choose between same restricted driver (as the envy install option) but it gives me only 640X480 resolution or less and the vesa driver is max. 800X600.  

I could at least use my older display at 1024X846 resolution in Gutsy.  When trying to install via Envy or changing the xorg.config file; it results in no login screen, a blinking cursor on a blank screen, after reboot, and log file shows nvidia kernel module is missing and no usable screens found -fatal server error! must overwrite conf file to vesa default in recovery mode.  Tried to remove & re-install glx as well but that did nothing.

I read about the manual install of a later nv driver version but that did not work for everyone, so I am taking a break first and hoping to hear about a fix on the way or clear advice since this is supposed to be long term support and I want to actually use Ubuntu Studio for its intended purposes someday! (Had many other problems with install prior-my fault- complicated multiboot!)
In passing if someone could tell me how to install the generic nv driver at least- what to write in xorg.config exactly to make that work like it did in Gutsy!


***Note: Sorry it looks like I had more than just nv driver installed and working in Gusty.
Also I managed to add generic nv to xorg.config file in Hardy (2.6.24.21rt) but nv default is using lower resolution and versions of glx than nvidia in Gutsy of course. So still a problem.

Here is my glxinfo with the restricted driver:
( while in vesa mode it showed libglx missing info for display info and RGB).  

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_swap_group
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_swap_group, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Quadro4 900 XGL/AGP/SSE2
OpenGL version string: 1.5.8 NVIDIA 96.43.05
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_HP_occlusion_test, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_clamp, GL_NV_fence, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_NV_texture_shader, 
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon

---

### Post by Neobuntu on 2008-11-10
> sudo dpkg-reconfigure -phigh xserver-xorg

Used to get me back to the nv driver so I could try again. I shouldn't think you'd have trouble with the Hardy nvidia installer ("hardware drivers" or something) because my GF4 works that way. I hope it's not broken with upgrades.

I'm trying to get the GF4 to work with my 1280x960 on boot in Intrepid and it requires clicking on the (Kubuntu) "Display" settings. Strange. I'm running the beta from Nvidia for Intrepid there. You shouldn't have to in Hardy LTS.

You are wise to stay with Hardy for a while.

---

### Post by WSmart on 2008-11-10
The issue in Ibex is the new restricted drivers interface, Jockey, or the lack of driver support with that and also the new xorg 1.5.  You have to enable the Intreprid Proposed software updates in the repository.

If you don't have jockey or xorg 1.5, you should be OK, though I wonder what would happen if you tried to use the new drivers there.....

You've got an older legacy card which makes me wonder because the Jockey/1.5 x issue is only with the two older driver sets, if it's 96 & 71.

---

### Post by streamsanddragonflies on 2008-11-11
> **WSmart said:**
> The issue in Ibex is the new restricted drivers interface, Jockey, or the lack of driver support with that and also the new xorg 1.5.  You have to enable the Intreprid Proposed software updates in the repository.

If you don't have jockey or xorg 1.5, you should be OK, though I wonder what would happen if you tried to use the new drivers there.....

You've got an older legacy card which makes me wonder because the Jockey/1.5 x issue is only with the two older driver sets, if it's 96 & 71.

Sorry, WSmart, I'm confused by your reference to Ibex, I think I do have jockey installed in Synaptic but It does not show as an app. anywhere, should I remove it?  I do have to use the 96.43 set in my Hardy 2.6.24-21-rt. 

 And by the way, with my attempt to have the default nv driver via xorg.conf, my xorg version is listed as "unknown" in my system info. app. and I forgot to mention that my screen does not even lay out correctly- some of the image is outside of the right border, about 1/2" almost!   

Because of the message I got via envy install- could it be I am missing a module?  Also if I use a newer screen, will it help any?

---

### Post by streamsanddragonflies on 2008-11-11
....> **Neobuntu said:**
> Used to get me back to the nv driver so I could try again. I shouldn't think you'd have trouble with the Hardy nvidia installer ("hardware drivers" or something) because my GF4 works that way. I hope it's not broken with upgrades.

I'm trying to get the GF4 to work with my 1280x960 on boot in Intrepid and it requires clicking on the (Kubuntu) "Display" settings. Strange. I'm running the beta from Nvidia for Intrepid there. You shouldn't have to in Hardy LTS.

You are wise to stay with Hardy for a while.

Thanks for your reply and suggestion, I am hoping to really get good desktop use out of hardy but this nvidia problem has me feeling less sure... did you see in my other reply that I mentionned that my screen position is also off?  I didn't quite know how to use the command you suggested before, if you are out of X environment due to a driver module missmatch, do you type that command and X then restarts? or do you let recovery mode fix X for you and then type it in the terminal once back in X?

Also by upgrade do you mean from Gutsy to Hardy (I have both seperate installs but Gutsy is on slower drive so I want to use Hardy for my multimedia work) or do you mean from 2.6.24-19-rt to 2.6.24-21-rt?  Can that new image "break" anything? Sorry for my noobiness!  I'm still not sure what is what yet (glx -is it the same one as the restricted driver (shows same exact version yet does not work via envy) and I just changed my repo to accepting pre-released updates as well, because I am wondering if I am missing some module that would help-is this a good idea?)

---

### Post by Neobuntu on 2008-11-12
The Nvidia "96" driver is out now(and works for me); for the Intrepid ibex 8.10 (Oct 2008) release. 8.10 though, is sadly not overall ready for prime time, yet.

The command I gave you is for getting back to a GUI in Hardy, after a failed direct (3D/DRI) Nvidia driver install attempt. 

Once you get it working with your preferred driver, use nvidia-settings...> sudo nvidia-settings... to pick your resolution **and saving it** with that utility program. Then you should reboot and notice your resolution as correct.

> sudo apt-get install nvidia-settings

If it's not installed.

---

### Post by streamsanddragonflies on 2008-11-27
Well I tried to manually install the latest driver available for Hardy LTS the NVIDIA 96.43.07 and after carefully following their instructions including removing certain modules and adding others from synaptic or apt, and installing from recovery in shell, the driver could not be installed.

  I am really at the end of my rope.  I had a hard time stopping gdm since my screen could not switch to console only-hence using recovery mode.  I tried to install the earlier driver via envy once again but that gave a blank screen again with the blinking cursor top left.

I have added my /var/log file just in case someone has a suggestion.  Keeping in mind that my other cheaper computer also uses the same driver for a similar card and identical monitor and it worked with Envy just fine!  Is it the rt kernel that is missing modules?  This rt kernel is meant for music production but for multimedia production as well.  It worked much better in Gutsy so I don't know why Nvidia and Ubuntu haven't found a fix for the LTS version... 

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Nov 27 00:55:19 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> Installing NVIDIA driver version 96.43.07.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-21-rt/build'
-> Kernel output path: '/lib/modules/2.6.24-21-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-21-rt/bu
   ild SYSOUT=/lib/modules/2.6.24-21-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-21-rt/build SUBDIRS=/tmp
   /selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL_
   _  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-ali
   asing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-flo
   at -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586
   -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86
   /mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-af
   ter-statement -Wno-pointer-sign   -I/tmp/selfgz5338/NVIDIA-Linux-x86-96.43.0
   7-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-su
   bscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"96.43.07\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE 
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)" -c -o /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/
   src/nv/.tmp_nv.o /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/n
   v.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function 'prefetch_range':
   include/linux/prefetch.h:57: warning: pointer of type 'void *' used in arith
   metic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function 'sg_virt':
   include/linux/scatterlist.h:293: warning: pointer of type 'void *' used in a
   rithmetic
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   '__nv_setup_pat_entries':
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:836: warning:
   comparison between signed and unsigned
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   '__nv_restore_pat_entries':
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:862: warning:
   comparison between signed and unsigned
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   'nv_kern_cpu_callback':
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:1188: warning
   : comparison between signed and unsigned
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:1195: warning
   : comparison between signed and unsigned
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   'nv_lock_init_locks':
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:3517: error: 
   implicit declaration of function '__SEMAPHORE_INITIALIZER'
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:3517: error: 
   invalid initializer
   /tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:3518: error: 
   invalid initializer
   make[3]: *** [/tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz5338/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

