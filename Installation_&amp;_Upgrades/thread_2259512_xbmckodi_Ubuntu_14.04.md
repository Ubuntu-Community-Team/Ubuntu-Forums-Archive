---
title: "xbmc/kodi Ubuntu 14.04"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by bandito40 on 2015-01-04
I got xbmc/kodi running flawlessly on my Chromebook by installing ChrUbuntu 12.04 however if I do a distro upgrade to Ubuntu 14.04 or install Ubuntu 14.04 I cannot get xbmc/kodi to run. I get an error "Kodi needs hardware acceleration OpenGL rendering. Install an appropriate driver." when I open xbmc/kodi in Ubuntu 14.04. I have tried various methods for install drivers but have no luck. Was wondering if anyone knows what I can do to resolve this issue. 


Thanks,

---

### Post by papibe on 2015-01-04
Hi bandito40.

Could you open a terminal, run these commands, and post back the result (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

apt-cache policy kodi xserver-xorg-video-intel  libva-intel-vaapi-driver
```
Regards.

---

### Post by catro on 2015-01-05
Hi, I got same problem while upgrading from XBMC to kodi. I'm running on Ubuntu 14.04.
Here's my output,
> lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0c)
        Subsystem: Intel Corporation Device [8086:2055]
        Kernel driver in use: i915


apt-cache policy kodi xserver-xorg-video-intel  libva-intel-vaapi-driver
kodi:
  Installed: 2:14.0~git20141223.1015-final-0trusty
  Candidate: 2:14.0~git20141223.1015-final-0trusty
  Version table:
 *** 2:14.0~git20141223.1015-final-0trusty 0
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
xserver-xorg-video-intel:
  Installed: 2:2.99.910-0ubuntu1.1
  Candidate: 2:2.99.910-0ubuntu1.3
  Version table:
     2:2.99.910-0ubuntu1.3 0
        500 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
 *** 2:2.99.910-0ubuntu1.1 0
        100 /var/lib/dpkg/status
     2:2.99.910-0ubuntu1 0
        500 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
libva-intel-vaapi-driver:
  Installed: 1.3.0-1ubuntu1
  Candidate: 1.3.0-1ubuntu1
  Version table:
 *** 1.3.0-1ubuntu1 0
        500 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status


---

### Post by bandito40 on 2015-01-05
Thanks for replying, here is the output.

lspci -nnk | grep -iA2 vga

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Lenovo Device [17aa:20e4]
	Kernel driver in use: i915
```

apt-cache policy kodi xserver-xorg-video-intel  libva-intel-vaapi-driver

```
aapi-driver
kodi:
  Installed: 2:14.0~git20141223.1015-final-0trusty
  Candidate: 2:14.0~git20141223.1015-final-0trusty
  Version table:
 *** 2:14.0~git20141223.1015-final-0trusty 0
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
xserver-xorg-video-intel:
  Installed: 2:2.99.910-0ubuntu1.3
  Candidate: 2:2.99.910-0ubuntu1.3
  Version table:
 *** 2:2.99.910-0ubuntu1.3 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2:2.99.910-0ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
libva-intel-vaapi-driver:
  Installed: 1.3.0-1ubuntu1
  Candidate: 1.3.0-1ubuntu1
  Version table:
 *** 1.3.0-1ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by papibe on 2015-01-05
Thanks. That looks OK.

If you upgraded the system, you may just need to restart. 

If that doesn't work. Let's check the OpenGL support. Could you run these commands, and post the output?
```
ldd $(which glxinfo)

glxinfo
```
Regards.

---

### Post by bandito40 on 2015-01-05
ldd $(which glxinfo)

```
	linux-vdso.so.1 =>  (0x00007fff907b0000)
	libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007fd3534c6000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fd353191000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fd352dca000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fd352ba0000)
	libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007fd352977000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fd352764000)
	libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007fd352561000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007fd35235b000)
	libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007fd352158000)
	libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007fd351f41000)
	libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007fd351d3c000)
	libxcb-dri3.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0 (0x00007fd351b38000)
	libxcb-present.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-present.so.0 (0x00007fd351935000)
	libxcb-sync.so.1 => /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1 (0x00007fd35172f000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fd35150f000)
	libxshmfence.so.1 => /usr/lib/x86_64-linux-gnu/libxshmfence.so.1 (0x00007fd35130d000)
	libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007fd351107000)
	libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007fd350efa000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fd350bf4000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fd3509d6000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fd3507d1000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fd353776000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fd3505cd000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fd3503c6000)


```

glxinfo

```

name of display: :0
Gen6+ requires Kernel 3.6 or later.

```

I attempted to upgrade to kernel 3.6 in hopes that it would resolve this issue but was not success in upgrading.

---

### Post by misswham2 on 2015-01-07
I just did an upgrade on my system and kodi was there.  What in the heck is this?  Is it an online storage system like cloud?  I got nervous because it was all over my screen and it took me a few to find out how to close it so it looked suspicious to me.

---

### Post by papibe on 2015-01-07
Hi misswham2.

I imagine you got XBMC from the XBMC/Kodi ppa, right?

Unfortunately, this could happen to software from ppas. They decided to change the software name, and when you upgrade you got the changes without any notice.

BTW, the version from the official repositories is still called XBMC.

Just a thought.
Regards.

---

### Post by ELMIT on 2015-06-22
I come today to that point. What do I need to do?

ldd $(which glxinfo)
	linux-vdso.so.1 =>  (0x00007ffd05bfc000)
	libGL.so.1 => /usr/lib/nvidia-346/libGL.so.1 (0x00007f2650631000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f26502fc000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f264ff36000)
	libnvidia-tls.so.346.72 => /usr/lib/nvidia-346/tls/libnvidia-tls.so.346.72 (0x00007f264fd33000)
	libnvidia-glcore.so.346.72 => /usr/lib/nvidia-346/libnvidia-glcore.so.346.72 (0x00007f264d058000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f264ce45000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f264cc41000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f264ca22000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f26509af000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f264c71b000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f264c517000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f264c311000)


glxinfo

name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_stereo_tree, GLX_EXT_swap_control, 
    GLX_EXT_swap_control_tear, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_NV_copy_image, 
    GLX_NV_delay_before_swap, GLX_NV_float_buffer, 
    GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_create_context_es_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, GLX_EXT_stereo_tree, 
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_copy_buffer, GLX_NV_copy_image, GLX_NV_delay_before_swap, 
    GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_NV_present_video, 
    GLX_NV_swap_group, GLX_NV_video_capture, GLX_NV_video_out, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, 
    GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_create_context_es_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_stereo_tree, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_copy_image, GLX_NV_delay_before_swap, GLX_NV_float_buffer, 
    GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 630/PCIe/SSE2
OpenGL version string: 2.1.2 NVIDIA 346.59
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, GL_ARB_clip_control, 
    GL_ARB_color_buffer_float, GL_ARB_compatibility, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_ARB_copy_image, GL_ARB_cull_distance, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_derivative_control, 
    GL_ARB_direct_state_access, GL_ARB_draw_buffers, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_texture_sub_image, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pipeline_statistics_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_shader_draw_parameters, GL_ARB_shader_group_vote, 
    GL_ARB_shader_image_size, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_image_samples, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_texture_barrier, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_levels, 

(The list is very long. I have no idea what I am looking for in it, nor want I bother you with an endless list)

---

