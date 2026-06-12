---
title: "3D does not work correctly after upgrading to 7.10"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Seb1982 on 2007-12-16
Hi everyone!

I recently upgraded my notebook's Ubuntu to 7.10. Sadly my 3D deskop doesn't work correctly (even if it does in the live environment). Here's what "glxinfo" answers:

```
seb@janee:~$ glxinfo
name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
seb@janee:~$ 

```

---

### Post by briandu on 2007-12-16
Do yourself a favour and download envy. You will find that all the scripts are fired off and initialised.

Good  luck

---

### Post by Seb1982 on 2007-12-17
I'm afraid this won't work. My notebook contains an Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller!

---

### Post by PmDematagoda on 2007-12-17
Do:-
```

sudo dpkg-reconfigure xserver-xorg
```

See if that solves your problem.

---

### Post by Seb1982 on 2007-12-17
Nope! I tried several settings but nothing changed. I even copied the "xorg.conf" file from the live environment where everything works correctly :( .

Any ideas? Please, reinstalling Ubuntu cannot be the solution!

---

### Post by Seb1982 on 2007-12-17
Is it possible that Swap is not mounted correctly? How do i check?

"top":
```
seb@janee:/etc$ top

top - 14:52:13 up 51 min,  2 users,  load average: 0.35, 0.40, 0.35
Tasks: 147 total,   2 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.8%us,  0.7%sy,  0.0%ni, 94.4%id,  0.0%wa,  2.2%hi,  0.0%si,  0.0%st
Mem:   1025872k total,   755468k used,   270404k free,    28316k buffers
Swap:  3004112k total,        0k used,  3004112k free,   357816k cached

```

---

### Post by Seb1982 on 2007-12-20
Bump!

---

### Post by PmDematagoda on 2007-12-20
What VGA card do you have?

---

### Post by Seb1982 on 2007-12-20
It's an internal Intel 945GM:

```
seb@janee:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

By the way, my desktop PC is facing the same problem. An ATI Radeon 9600 Pro is installed here.

```
seb@myra:~$ lspci | grep Display
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

```

Due to the fact that the same problem occurs on both systems i believe it has to do with my former configuration in 7.04. Any ideas???

Thanks a lot for help!

Seb

---

### Post by igknighted on 2007-12-20
Did you do an upgrade or a fresh install?  An upgrade can mess things up like this.

---

### Post by Seb1982 on 2007-12-20
I upgraded both computers.

---

### Post by igknighted on 2007-12-20
> **Seb1982 said:**
> I upgraded both computers.

Upgrades are often un-successful.  I would wager this is your problem, especially since there were major changes to xorg between fiesty and gutsy.

EDIT: That is not to say it cannot be fixed.

---

### Post by Seb1982 on 2007-12-22
Is there nothing i can do?

---

