---
title: "Cannot install Chrome"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2017-03-08
Hi:

I uninstalled it because it ceased to work after trying to install the lates Flash version. Now I try t install stable version from Software Center and get this:

```
Packet dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies: 

google-chrome-stable: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                      Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.3 is to be installed
                      Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.3-2build1 is to be installed
                      Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
                      Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1~precise3 is to be installed
                      Depends: libxrandr2 (>= 2:1.2.99.3) but 2:1.3.2-2ubuntu0.3 is to be installed
```

even in Terminal:
```
sudo apt-get install google-chrome stable

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package google-chrome is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'google-chrome' has no installation candidate
E: Unable to locate package stable
```

Help!

---

### Post by Autodave on 2017-03-08
For some reason, I do not believe that Chrome is available any longer. Chromium is, though.  

Hopefully, someone else will have a better answer for you.

---

### Post by rva1945 on 2017-03-08
Yes Chromium is available and I installed it. But now I can't install the flash plugin.
This
sudo apt-get install pepperflashplugin-nonfree
gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pepperflashplugin-nonfree
```

---

### Post by rva1945 on 2017-03-08
In Software Center, Adobe Flash Plugin appears as Installed. But in Chromium, chrome//flash says

[COLOR=#000000][FONT=Ubuntu][h=1]About Flash[/h][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][TABLE]
[TR]
[TD]**Chromium**[/TD]
[TD]37.0.2062.120 (Ubuntu 12.04)[/TD]
[/TR]
[TR]
[TD]**OS**[/TD]
[TD]Linux[/TD]
[/TR]
[TR]
[TD]**Flash plugin**[/TD]
[TD]Not installed[/TD]
[/TR]
[TR]
[TD]****
[/TD]
[TD]--- Crash data ---[/TD]
[/TR]
[TR]
[TD]**Crash Reporting**[/TD]
[TD]Enable crash reporting to see crash IDs[/TD]
[/TR]
[TR]
[TD]**For more details**[/TD]
[TD]https://support.google.com/chrome/?p=ui_usagestat[/TD]
[/TR]
[TR]
[TD]****
[/TD]
[TD]--- GPU information ---[/TD]
[/TR]
[TR]
[TD]**WARNING:**[/TD]
[TD]GPU access is not allowed: Features are disabled upon full but not preliminary GPU info.[/TD]
[/TR]
[TR]
[TD]****
[/TD]
[TD]--- GPU driver, more information ---[/TD]
[/TR]
[TR]
[TD]**Vendor Id**[/TD]
[TD]0x8086[/TD]
[/TR]
[TR]
[TD]**Device Id**[/TD]
[TD]0x0412[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]Mesa[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]8.0.4[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD]
[/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]1.20[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]1.20[/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]VMware, Inc.[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]Gallium 0.4 on llvmpipe (LLVM 0x300)[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]2.1 Mesa 8.0.4[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_compression_latc GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_draw_buffers_blend GL_ARB_ES2_compatibility GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_shader_texture_lod GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness GL_ARB_texture_storage[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by howefield on 2017-03-09
Are you running Ubuntu 12.04 ?

---

### Post by rva1945 on 2017-03-09
Yep.

---

### Post by RobGoss on 2017-03-09
Is this a 32 bit system or a 64 bit, the reason I ask is because Google has drop support for the 32 bit version of Google Chrome sometime ago they only have Chromium or the 64 bit Google chrome

---

### Post by rva1945 on 2017-03-09
64-bit

---

### Post by howefield on 2017-03-10
> **rva1945 said:**
> Yep.

Ok, with support for 12.04 expiring next month it may not be worth spending the time fixing the issue. The best way to install flash is to enable the Canonical Partners repository and use the adobe-flashplugin package (after first purging existing flash packages).

Chrome would generally be installed by downloading the deb package via the Chrome website, I'd suggest using ppa-purge to get rid of any Chrome repositories that you have added and use the currently available deb package from the Chrome website.

---

### Post by RobGoss on 2017-03-10
+1 Howe field

I've always downloaded and installed, Google Chrome from their main website without and issues...

---

