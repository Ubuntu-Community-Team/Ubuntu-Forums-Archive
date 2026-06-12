---
title: "How to install ATI Radeon 9100IGP driver in ubuntu 11.04"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by ashah98 on 2011-05-06
I have clean install the Ubuntu v 11.04 on my desktop PC but unable to install the driver for my integrated ATI Radeon 9100 IGP on Asus Motherboard.

Please help to resolve this issue.

lspci -nn | grep VGA

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon 9100 IGP [1002:5834]

---

### Post by Blasphemist on 2011-05-06
This seems to be a bit other than straightforward and easy for the ATI drivers. See this page.

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)

You have these options.

> Users with ATI cards have the following driver options:
vesa - very basic, lacks 2D/3D acceleration, and focuses on compatibility with all VESA-compliant graphics cards. It is good for starting the GUI environment when no accelerated driver is available/working and little else.
ati - actually a thin wrapper that will invoke the radeon driver (or another ati open-source driver for pre-Radeon cards).
radeon - open source driver supporting all Radeon cards. This driver has excellent 2D acceleration and compatibility with the Linux graphics stack. 3D acceleration is sufficient for desktop effects and a nice set of native Linux games. Power management is now comparable to the Catalyst driver.
radeonhd - an alternate driver supporting R520-R7x0 hardware. This driver is now officially deprecated in favor of radeon. If you still want to try it, see: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
Catalyst (a.k.a fglrx) a proprietary "blob" (closed source binary) driver designed by ATI, with 3D code based off of their Windows driver. Only RadeonHD chips are supported on recent Linux distros.

These are the updated open source driver ppa's.

> "Ubuntu-X" : This PPA offers the latest stable releases of video driver-related components. Follow the instructions at: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Xorg-edgers: This bleeding-edge PPA offers video driver-related components straight from their code (git) repositories. Follow the instructions at: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
[edit]

---

### Post by Blasphemist on 2011-05-06
I'll add this too. This is specific to natty and the recommendations for it. It does discuss recommendations specific to ati and there can be issues.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

### Post by ashah98 on 2011-05-07
Dear I have used the method as mentioned in links referred by you but still no luck.

I also have downloaded the appropriate driver from ATI support site and when install through terminal there is a error following message;

root@ubuntu:/home/amir/Downloads# sudo sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
root@ubuntu:/home/amir/Downloads# 


I have Asus Motherboard which have built-in AGP chip of ATI 9100 IGP.
I am using Ubuntu 11.04 version 32bit

Please help to resolve this problem.

---

### Post by Blasphemist on 2011-05-07
Should we work on installing the radeon open source drivers? It looks like you tried installing an old driver set for an old version of X. Look at this page. It walks you through what to do. I wish I'd found it earlier.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Do make sure to follow the link to this page and fully purge fglrx.

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by ashah98 on 2011-05-14
Dear Blasphemist,

I have used the method as mentioned is link but still not succeeded. I will be great full if you read the log & further suggest me. Thanks in advance
Here is the log of process execution; 


[B]root@ubuntu:/home/amir# sudo /usr/share/ati/fglrx-uninstall.sh
sudo: /usr/share/ati/fglrx-uninstall.sh: command not found

root@ubuntu:/home/amir# sudo apt-get remove --purge fglrx*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages will be REMOVED:
  fglrx*
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

root@ubuntu:/home/amir# sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-video-ati* xserver-xorg-video-radeon*
0 upgraded, 0 newly installed, 2 to remove and 6 not upgraded.
After this operation, 1,380 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 134448 files and directories currently installed.)
Removing xserver-xorg-video-ati ...
Removing xserver-xorg-video-radeon ...
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...

root@ubuntu:/home/amir# sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xserver-xorg-video-radeon
Suggested packages:
  firmware-linux
The following NEW packages will be installed:
  xserver-xorg-video-ati xserver-xorg-video-radeon
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 465 kB of archives.
After this operation, 1,380 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) natty/main xserver-xorg-video-radeon i386 1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt [444 kB]
Get:2 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) natty/main xserver-xorg-video-ati i386 1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt [21.9 kB]
Fetched 465 kB in 10s (44.2 kB/s)                                              
Selecting previously deselected package xserver-xorg-video-radeon.
(Reading database ... 134430 files and directories currently installed.)
Unpacking xserver-xorg-video-radeon (from .../xserver-xorg-video-radeon_1%3a6.14.99+git20110508.90abffbd-0ubuntu0sarvatt_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-ati.
Unpacking xserver-xorg-video-ati (from .../xserver-xorg-video-ati_1%3a6.14.99+git20110508.90abffbd-0ubuntu0sarvatt_i386.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-radeon (1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt) ...
Setting up xserver-xorg-video-ati (1:6.14.99+git20110508.90abffbd-0ubuntu0sarvatt) ...

root@ubuntu:/home/amir# sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglapi-mesa
Suggested packages:
  libglide3
The following packages will be upgraded:
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
3 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 8,799 kB/10.4 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) natty/main libgl1-mesa-dri i386 7.11.0+git20110509.7074801e-0ubuntu0sarvatt [8,627 kB]
Get:2 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) natty/main libgl1-mesa-glx i386 7.11.0+git20110509.7074801e-0ubuntu0sarvatt [119 kB]
Get:3 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) natty/main libglapi-mesa i386 7.11.0+git20110509.7074801e-0ubuntu0sarvatt [52.3 kB]
Fetched 8,799 kB in 1min 37s (90.7 kB/s)                                       
(Reading database ... 134449 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.11.0+git20110504.37058c34-0ubuntu0sarvatt (using .../libgl1-mesa-dri_7.11.0+git20110509.7074801e-0ubuntu0sarvatt_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.11.0+git20110504.37058c34-0ubuntu0sarvatt (using .../libgl1-mesa-glx_7.11.0+git20110509.7074801e-0ubuntu0sarvatt_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace libglapi-mesa 7.11.0+git20110504.37058c34-0ubuntu0sarvatt (using .../libglapi-mesa_7.11.0+git20110509.7074801e-0ubuntu0sarvatt_i386.deb) ...
Unpacking replacement libglapi-mesa ...
Preparing to replace xserver-xorg-core 2:1.10.1+git20110429+server-1.10-branch.b4455b11-0ubuntu0sarvatt (using .../xserver-xorg-core_2%3a1.10.1+git20110429+server-1.10-branch.b4455b11-0ubuntu0sarvatt_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Processing triggers for man-db ...
Setting up libgl1-mesa-dri (7.11.0+git20110509.7074801e-0ubuntu0sarvatt) ...
Setting up libglapi-mesa (7.11.0+git20110509.7074801e-0ubuntu0sarvatt) ...
Setting up libgl1-mesa-glx (7.11.0+git20110509.7074801e-0ubuntu0sarvatt) ...
Setting up xserver-xorg-core (2:1.10.1+git20110429+server-1.10-branch.b4455b11-0ubuntu0sarvatt) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

root@ubuntu:/home/amir# sudo dpkg-reconfigure xserver-xorg
root@ubuntu:/home/amir# 
[/B]

---

### Post by Blasphemist on 2011-05-14
What is happening now? Are there things still not working? Did you do the following?
> _Testing The Driver_
To see if your driver uses KMS (Kernel Mode Setting), run command

dmesg | grep drm
This should indicate that the drm got initialized and set up, with maybe mention of the framebuffer and modes set. E.g.:

[    2.699321] [drm] Initialized drm 1.1.0 20060810
[    5.700397] [drm] radeon kernel modesetting enabled.
[    5.701871] [drm] initializing kernel modesetting (RV710 0x1002:0x9540).
...
To see your OpenGL information, you can run:

LIBGL_DEBUG=verbose glxinfo
Make sure your OpenGL renderer string does not say "software rasterizer" because that would mean you have no 3D hardware acceleration.

If something isn't working, it looks like you'll need to use KernelModeSetting. I see that the link for that isn't current. I'll find the current and post that.
Also, rerun this please and post its results.
/usr/lib/nux/unity_support_test -p

---

### Post by Blasphemist on 2011-05-14
See post number 1 in this thread on natty kernelmodesetting.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

This section is on permanent settings like you'll need.
**How to permanently set kernel boot options on an installed OS (not wubi)**
Usually nomodeset is the first to try but what to try depends on the issue.

---

### Post by ashah98 on 2011-05-15
Dear Blasphemist,

I have run the command as mentioned directed by you and following is the log;


[B]root@ubuntu:/home/amir# dmesg | grep drm
[   13.459412] [drm] Initialized drm 1.1.0 20060810
[   13.866470] [drm] radeon defaulting to kernel modesetting.
[   13.866476] [drm] radeon kernel modesetting enabled.
[   13.876847] [drm] initializing kernel modesetting (RS300 0x1002:0x5834).
[   13.876893] [drm] register mmio base: 0xE5000000
[   13.876895] [drm] register mmio size: 65536
[   13.877136] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.877139] [drm] Driver supports precise vblank timestamp query.
[   13.877173] [drm] radeon: irq initialized.
[   13.877370] [drm] Detected VRAM RAM=128M, BAR=256M
[   13.877375] [drm] RAM width 128bits DDR
[   13.881188] [drm] radeon: 128M of VRAM memory ready
[   13.881192] [drm] radeon: 64M of GTT memory ready.
[   13.883327] [drm] Loading R200 Microcode
[   13.891672] [drm] radeon: ring at 0x00000000E0001000
[   13.891691] [drm] ring test succeeded in 0 usecs
[   13.892247] [drm] radeon: ib pool ready.
[   13.892331] [drm] ib test succeeded in 0 usecs
[   13.896804] [drm] No valid Ext TMDS info found in BIOS
[   13.899873] [drm] Radeon Display Connectors
[   13.899878] [drm] Connector 0:
[   13.899881] [drm]   VGA
[   13.899884] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   13.899886] [drm]   Encoders:
[   13.899888] [drm]     CRT1: INTERNAL_DAC2
[   13.899890] [drm] Connector 1:
[   13.899892] [drm]   DVI-D
[   13.899893] [drm]   HPD2
[   13.899896] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   13.899898] [drm]   Encoders:
[   13.899900] [drm]     DFP2: INTERNAL_DVO1
[   13.899902] [drm] Connector 2:
[   13.899903] [drm]   S-video
[   13.899905] [drm]   Encoders:
[   13.899907] [drm]     TV1: INTERNAL_DAC2
[   14.069151] [drm] fb mappable at 0xD0040000
[   14.069156] [drm] vram apper at 0xD0000000
[   14.069158] [drm] size 3145728
[   14.069160] [drm] fb depth is 24
[   14.069161] [drm]    pitch is 4096
[   14.070646] fb0: radeondrmfb frame buffer device
[   14.070648] drm: registered panic notifier
[   14.070662] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
root@ubuntu:/home/amir# LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/dri/tls/r200_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: failed to create dri screen
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_paletted_texture, GL_EXT_polygon_offset, 
    GL_EXT_subtexture, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_EXT_compiled_vertex_array, GL_EXT_texture, GL_EXT_texture3D, 
    GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_MESA_resize_buffers, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_S3_s3tc, GL_SUN_multi_draw_arrays, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_EXT_framebuffer_object, GL_EXT_shared_texture_palette, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_dot3, 
    GL_MESA_window_pos, GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, 
    GL_NV_vertex_program, GL_ARB_depth_texture, GL_ARB_occlusion_query, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, 
    GL_NV_depth_clamp, GL_NV_fragment_program, GL_NV_point_sprite, 
    GL_NV_vertex_program1_1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_depth_bounds_test, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert, 
    GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_NV_fragment_program_option, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_gpu_program_parameters, 
    GL_EXT_texture_array, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_env_combine, GL_EXT_texture_sRGB_decode, 
    GL_MESA_texture_array, GL_ARB_copy_buffer, GL_ARB_draw_instanced, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_texture_rg, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_EXT_provoking_vertex, GL_ARB_robustness

64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0e1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ea 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ed 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ee 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0fa 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0fd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0fe 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0ff 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x100 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x101 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x102 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x103 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x104 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x105 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x106 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x107 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x108 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x109 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x10a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x10b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x10c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x10d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x10e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x10f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x110 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x111 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x112 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x113 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x114 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x115 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x116 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x117 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x118 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x119 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x11a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x11b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x11c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x11d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x060 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x061  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x063  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x064  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x065  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x066  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x067  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x068  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x069  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x06a  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x06b  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x06c  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x06d  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x06e  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x06f  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x070  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x071  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x075  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x076  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x078  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x079  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x07d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x07e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x07f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x081 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x082 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x083 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x085 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x086 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x087 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x088 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x089 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x08b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x08d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x095 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x09a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x09b 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x09d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a1  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a3  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a5  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a6  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0a7  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a8  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0a9  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x0aa  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x0ab  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x0ac  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x0ad  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x0ae  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x0af  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x0b0  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x0b1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0b3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0b5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0b6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0b7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0b8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0b9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0ba  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0bb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0bc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0bd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0be  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0c0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0c1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0c7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0c9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ca 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0cd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ce 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0d7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0d9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0da 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0db 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0dc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0dd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0de 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0df 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0e0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

root@ubuntu:/home/amir# /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.11-devel

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
root@ubuntu:/home/amir# 
[/B]

Kindly review the log and further suggest me.

Thanks for your ultimate support and guidance.

Regards,
Amir

---

