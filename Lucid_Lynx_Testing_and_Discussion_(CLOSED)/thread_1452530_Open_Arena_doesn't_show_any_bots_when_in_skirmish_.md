---
title: "Open Arena doesn't show any bots when in skirmish or regular play mode (LUCID LYNX)"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rhmarras on 2010-04-12
Hi, I just upgraded to Lucid Lynx Beta
Linux xxxxxxx 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
I went to play Open Arena 0.8.1-6 (repositories version which was working perfectly before upgrade) and when I go into normal play mode the only player that enters the arena is me. I tried in skirmish mode adding other bots and still the same, just me. Then I downloaded the patch for 0.8.5, applied it and the patch worked OK but still the same problem of just me.
other than that, the game works perfect. (just pretty boring shooting at the walls)
As a try, I purged the installation, removed all config files, etc, and then reinstalled from ubuntu repositories. Nothing changed, still the same error.

Please check the output in here:

```
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 
GL_VERSION: 2.1 Mesa 7.7.1
GL_EXTENSIONS: GL_EXT_compiled_vertex_array GL_EXT_texture_env_add GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_depth_clamp GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_envmap_bumpmap GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_texture_signed_rgba GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
----- FS_Startup -----
Current search path:
/home/username/.openarena/baseoa/pak6-patch085.pk3 (559 files)
/home/username/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
18888 files in pk3 files
Loading vm file vm/qagame.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1564 jump table targets
total 0, hsize 1021, zero 1021, min 0, max 0
total 23318, hsize 1021, zero 0, min 4, max 48
VM file qagame compiled to 7198928 bytes of code (0x7f4140574000 - 0x7f4140c518d0)
compilation took 2.766619 seconds
qagame loaded in 3000544 bytes on the hunk
------- Game Initialization -------
gamename: baseoa
gamedate: Jan  3 2010
Not logging to disk.
Gametype changed, clearing session data.
^3!readconfig: ^7could not open admin config file admin.dat
Sprees/Kills: loaded 1 killing sprees, 0 death sprees, and 0 multikills.
0 teams with 0 entities
19 items registered
-----------------------------------
------- BotLib Initialization -------
loaded weapons.c
loaded items.c
loaded syn.c
loaded rnd.c
^1Error: file match.c, line 24: file matchh" not found
loaded match.c
loaded rchat.c
------------ Map Loading ------------
trying to load maps/oa_dm1.aas
loaded maps/oa_dm1.aas
item_armor_combat in solid at (-392.0 1116.0 32.0)
ammo_cells not reachable for bots at (1117.0 188.0 -28.0)
item_armor_shard in solid at (-385.0 666.0 24.0)
item_armor_shard not reachable for bots at (-385.0 666.0 24.0)
item_armor_shard in solid at (-129.0 666.0 24.0)
item_armor_shard not reachable for bots at (-129.0 666.0 24.0)
ammo_blllets not reachable for bots at (-639.0 1998.0 -76.0)
item_armor_shard in solid at (-193.0 666.0 24.0)
item_armor_shard not reachable for bots at (-193.0 666.0 24.0)
item_armor_shard in solid at (-257.0 666.0 24.0)
item_armor_shard not reachable for bots at (-257.0 666.0 24.0)
item_armor_shard in solid at (-319.0 666.0 24.0)
item_armor_shard not reachable for bots at (-319.0 666.0 24.0)
ammo_heells in solid at (-21.0 1011.0 32.0)
ammo_rcckets not reachable for bots at (-515.0 344.0 -76.0)
found 30 level items
-------------------------------------
24 bots parsed
51 arenas parsed
AAS initialized.
-----------------------------------
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't find skill 1 in bots/default_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't load any skill from bots/default_c.c
^1Error: file bots/merman_c.c, line 24: file charsh" not found
^3Warning: couldn't find skill 1 in bots/merman_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/merman_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't load any skill from bots/merman_c.c
^1Fatal: couldn't load skill 2.000000 from bots/merman_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't find skill 1 in bots/default_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't load any skill from bots/default_c.c
^1Error: file bots/major_c.c, line 24: file charsh" not found
^3Warning: couldn't find skill 1 in bots/major_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/major_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't load any skill from bots/major_c.c
^1Fatal: couldn't load skill 2.000000 from bots/major_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't find skill 1 in bots/default_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't load any skill from bots/default_c.c
^1Error: file bots/kyonshi_c.c, line 24: file charsh" not found
^3Warning: couldn't find skill 1 in bots/kyonshi_c.c
^1Error: file bots/default_c.c, line 24: file charsh" not found
^1Error: file bots/kyonshi_c.c, line 24: file charsh" not found
^1Error: file bots/default_c.c, line 24: file charsh" not found
^3Warning: couldn't load any skill from bots/kyonshi_c.c
^1Fatal: couldn't load skill 2.000000 from bots/kyonshi_c.c
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 
GL_VERSION: 2.1 Mesa 7.7.1
GL_EXTENSIONS: GL_EXT_compiled_vertex_array GL_EXT_texture_env_add GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_depth_clamp GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_envmap_bumpmap GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_texture_signed_rgba GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1550 jump table targets
total 0, hsize 1021, zero 1021, min 0, max 0
total 10042, hsize 1021, zero 2, min 0, max 30
VM file ui compiled to 3203472 bytes of code (0x7f414115d000 - 0x7f414146b190)
compilation took 1.193370 seconds
ui loaded in 1450816 bytes on the hunk
51 arenas parsed
1 arenas ignored to make count divisible by 4
24 bots parsed
^3WARNING: unknown blend mode 'gl_one_minus_dst_color' in shader 'menuback_blueish', substituting GL_ONE
Loading vm file vm/cgame.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1227 jump table targets
total 0, hsize 1021, zero 1021, min 0, max 0
total 10889, hsize 1021, zero 1, min 0, max 29
VM file cgame compiled to 4145957 bytes of code (0x7f414017f000 - 0x7f4140573325)
compilation took 1.558465 seconds
cgame loaded in 4725504 bytes on the hunk
stitched 0 LoD cracks
...loaded 882 faces, 0 meshes, 10 trisurfs, 10 flares
WARNING: reused image textures/flares/flarey.tga with mixed glWrapClampMode parm
WARNING: reused image textures/flares/lava.tga with mixed glWrapClampMode parm
^3WARNING: R_FindImageFile could not find 'models/players/smarine/l_legs.tga' in shader 'models/players/smarine/l_legs'
^3Shader models/players/smarine/l_legs has a stage with no image
^3WARNING: R_FindImageFile could not find 'models/players/smarine/u_torso.tga' in shader 'models/players/smarine/u_torso'
^3Shader models/players/smarine/u_torso has a stage with no image
^3WARNING: R_FindImageFile could not find 'models/players/smarine/h_head.tga' in shader 'models/players/smarine/h_head'
^3Shader models/players/smarine/h_head has a stage with no image
Can't read sound file music/sonic6.ogg
CL_InitCGame:  3.81 seconds
29 msec to draw all images
Com_TouchMemory: 0 msec
Shbalanke^7 entered the game
----- Server Shutdown (Server quit) -----
==== ShutdownGame ====
AAS shutdown.
---------------------------
----- CL_Shutdown -----
AL lib: ALc.c:1808: alcCloseDevice(): deleting 9 Buffer(s)
OpenAL capture device closed.
RE_Shutdown( 1 )
-----------------------
```

Any hints?

---

### Post by rhmarras on 2010-04-13
update.
I have deployed the 32 bit version over the same OS and it works fine.
strange, uh?

---

