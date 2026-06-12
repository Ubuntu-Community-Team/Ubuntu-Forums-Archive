---
title: "opengl problem(not sure where to put this srry)"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by youri on 2005-05-22
i cant seem to get opengl working on my ubuntu installation what did i do wrong? here is the verbose output of glxgears(yes opengl is installed):
```

Window x=0, y=0, width=300, height=300
[sis_alloc.c:154]: Failure to allocate Z buffer.

```

and if its of some use heres glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIS_multisample,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20040925 AGP 1x x86/MMX+/3DNow!+
OpenGL version string: 1.2 Mesa 6.2.1
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, GL_MESA_window_pos,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x26 16 tc  0 16  0 r  .  .  5  6  5  0  0 32  0  0  0  0  0  0 0 None
0x27 16 tc  0 16  0 r  y  .  5  6  5  0  0 32  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x2c 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2d 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 tc  0 16  0 r  .  .  5  6  5  0  0 32  0 16 16 16  0  0 0 Slow
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  0 32  0 16 16 16  0  0 0 Slow
0x30 16 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x31 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow

```

my vidcard is a sis730
i have some experience with slackware but this never happened in slackware does anyone knows what the problem is?

---

