---
title: "How to force-install a .run file?"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by deadlylady on 2012-11-30
I'm having troubles with my graphic card.

I was guided to [COLOR=Blue]*[this]("http://ubuntuforums.org/showthread.php?t=2085133&highlight=Radeon+HD+7700")*[/COLOR] thread from another thread I started and thought I found the solution in a [COLOR=Blue]*[new driver]("http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx")*[/COLOR] for my card. 

However the installer won't let me install:

>                                                   One or more tools required for installation cannot be found on the system.
Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
See /usr/share/ati/fglrx-install.log for more details.                                 
The install-log dosen't exist in the given path during the  installation-process and afterwards the entire folder disappears. Nor  does a search for the logfile render any hits, hence I do not know what  "required tools" I should be downloading?
 
I looked up [COLOR=Blue]*[force-installing ]("http://askubuntu.com/questions/104225/how-do-i-force-install-a-run")*[/COLOR]and  tried the advise offered but they both resulted in previous  result(above error-message). Is it even advisable to force-install and  if so how do I do it seeing that the "chmod a+x *.run" and "sudo  ./*.run" commands aren't doing it?

---

### Post by mastablasta on 2012-11-30
have you read here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
chmod command make the file executable sudo elevates privileges to root power so you can run the file that makes systemwide changes.
 
can you copy (mark text with mouse, right click it, then copy) and post here what you put in terminal and what it gives you out?

---

### Post by dino99 on 2012-11-30
Terminal Method

Assume the file is called some-app.run and is in the folder /home/user/Downloads. You will need to modify these instructions to fit your situation.

enter cd /home/user/Downloads

sudo chmod +x some-app.run
sudo sh ./some-app.run

---

### Post by deadlylady on 2012-12-04
> **mastablasta said:**
> have you read here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
chmod command make the file executable sudo elevates privileges to root  power so you can run the file that makes systemwide changes.
 
can you copy (mark text with mouse, right click it, then copy) and post  here what you put in terminal and what it gives you out?
Yes I've done that check-list and as far as I understand it's compatible:
> 01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cape Verde [Radeon HD 7700 Series] [1002:683d] (prog-if 00 [VGA controller])> **dino99 said:**
> Terminal Method

Assume the file is called some-app.run and is in the folder  /home/user/Downloads. You will need to modify these instructions to fit  your situation.

[B]enter cd /home/user/Downloads

sudo chmod +x some-app.run
sudo sh ./some-app.run[/B]
I don't know if I was unclear in my post but this IS what I have been  trying to do, that's when i get the following error-message from the  INSTALLER not from the terminal as I understand it. I just tried it  again exactly the way you wrote dino99, and I get the error message from  the installer:
                                                                                > One or more tools required for installation cannot be  found on the system.
Install the required tools before installing the fglrx driver.   Optionally, run the installer with --force option to install without the   tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
See /usr/share/ati/fglrx-install.log for more details.                       So what - is it telling me to force-install although I'm  already forceinstalling? 

This is what appears in the Terminal itself:
> p@p-desktop:~$ cd ~/Desktop
p@p-desktop:~/Desktop$ ls
amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.run  todo 15-11-2012~  todo 29-11-2012~
Another link to todo 15-11-2012~                          todo 29-11-2012
p@p-desktop:~/Desktop$ sudo chmod +x amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.run
p@p-desktop:~/Desktop$ sudo sh ./amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.run
Created directory fglrx-install.3BDHhd
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary  Driver-9.01.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
loki_setup: directory: (null)
Sorry if I missed something, I am a total newbie at this, thanks for any elaboration if I missed something

---

### Post by element6 on 2012-12-04
If I may speculate, you are trying to install the latest catalyst drivers via the "run" file?  If yes, i did the same thing and got the same missing tools error.  I was able to solve the issue by completing the following:

> [INDENT]sudo apt-get install linux-source
sudo apt-get install linux-headers-3.5.0-17-generic[/INDENT]

I am an extreme newbie and dont know why it worked, but it did.  I posted a little write up, along with proper credit [http://www.411overkill.com/viewtopic.php?f=104&t=8285]("http://www.411overkill.com/viewtopic.php?f=104&t=8285")

---

### Post by deadlylady on 2012-12-04
> **element6 said:**
> If I may speculate, you are trying to install the latest catalyst drivers via the "run" file?  If yes, i did the same thing and got the same missing tools error.  I was able to solve the issue by completing the following:



I am an extreme newbie and dont know why it worked, but it did.  I posted a little write up, along with proper credit [http://www.411overkill.com/viewtopic.php?f=104&t=8285](http://www.411overkill.com/viewtopic.php?f=104&t=8285)
Ok, thank you tried this, it installed a bunch of stuff and everything went well except installing the amd-driver, same error:
                             > One or more tools required for installation cannot be  found on the system.
Install the required tools before installing the fglrx driver.    Optionally, run the installer with --force option to install without the    tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
See /usr/share/ati/fglrx-install.log for more details.                      
Edit: Actually I think I somehow managed to install the driver from a guide linked by a user in my other thread on my problems with graphics card and ubuntu:
[http://ubuntuforums.org/showthread.php?t=2088463](http://ubuntuforums.org/showthread.php?t=2088463)
But it still didn't solve my overall problems. But I think it installed the driver, although according to the method described in this thread I am lacking some necessary components

---

### Post by darkod on 2012-12-04
I don't know 100% what the .run file is trying to install, but it seems to get stuck at installing fglrx. Since that is a separate package too, try installing it yourself first:
sudo apt-get install fglrx

In fact, I have seen posts about installing ATI drivers where they only install the fglrx and don't install any .run files after that.

---

### Post by element6 on 2012-12-04
Hummm..... Im trying to think back to my marathon weekend which got rid of the error.  The only other thing I did was install some libs per:

> sudo apt-get install ia32-libs-multiarch i386 lib32gcc1 libc6-i386

Then try installing the ATI driver:

> sudo sh ./ati-driver-installer-catalyst-12.10-x86.x86_64.run (or whatever driver you are trying to install)

Once again, the link: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx)

Let me know if it works.

EDIT: I did the install for 64bit.

---

### Post by darkod on 2012-12-04
Have you tried visiting the support section of the AMD website?

If you select to download the linux drivers for your specific card, it also has a link to unofficial wiki. In there, there is actually a section about installing drivers for ubuntu:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Just select your version and follow it. It actually says the most common way to install is simply installing fglrx from the ubuntu repositories.

As far as the .run file is concerned, the instructions say you use it to create .deb file. It's not used to install directly. The command to create the .deb is different to the one you tried to install with, so those messages might be because of that.

The wiki covers a few different install procedures including removing older existing drivers if you need to do that.

---

### Post by darkod on 2012-12-04
PS. You also have these instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

In the Manually Installing Catalyst 12.6 section it also mentions the command to create .deb file from the .run, which also confirms you need to do that. The .run doesn't seem to install the driver by itself.

---

### Post by element6 on 2012-12-04
> **darkod said:**
> PS. You also have these instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

In the Manually Installing Catalyst 12.6 section it also mentions the command to create .deb file from the .run, which also confirms you need to do that. The .run doesn't seem to install the driver by itself.

Creating the debs is the long and hard road (which I did as well, but did not work).  The simple way is to follow the AMD release notes instructions.  If you do this, you get the error the poster stated.  To solve it, I installed the headers per my previous post and I guess the lib32s as described in the subsequent post.  

Once you start the  run file, a AMD graphical interface pops and it and guides you through the install.  The hang up was once the interface is running, and error pops up stating there are missing tools.  I got this several times until I finally installed the headers and libs.  Then the error went away and the AMD driver installed.

---

### Post by darkod on 2012-12-04
> **element6 said:**
> Creating the debs is the long and hard road (which I did as well, but did not work).  The simple way is to follow the AMD release notes instructions.  If you do this, you get the error the poster stated.  To solve it, I installed the headers per my previous post and I guess the lib32s as described in the subsequent post.  

Once you start the  run file, a AMD graphical interface pops and it and guides you through the install.  The hang up was once the interface is running, and error pops up stating there are missing tools.  I got this several times until I finally installed the headers and libs.  Then the error went away and the AMD driver installed.

It might have worked for you (after several tries which another user might not handle as you did) and I mean no disrespect, but AMD instructions also say to create the .deb if installing the manual way.
So, I prefer to recommend the instructions of the manufacturer.

The quick way without creating debs, and what AMD also calls safest, is in the instructions too:
```
sudo apt-get install fglrx fglrx-amdcccle
```

You won't have the latest Catalyst version, but it is quick and should be safe, and it still installs Catalyst.

---

### Post by deadlylady on 2012-12-04
> **darkod said:**
> I don't know 100% what the .run file is trying to install, but it seems to get stuck at installing fglrx. Since that is a separate package too, try installing it yourself first:
sudo apt-get install fglrx

In fact, I have seen posts about installing ATI drivers where they only install the fglrx and don't install any .run files after that.
:/
Installing that package seemed to get me further away from compatibility:
> Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
**GL vertex buffer object:  no**
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       noBefore the GL vertex buffer object read "yes"!?

And afterwards I tried installing the driver again but the same error followed.

Should I delete the package again?

Edit: after restart my desktop was very messed up, the fglrx package dosen't play with my system in it's current state and comes with the ati binary package that I have had problems with earlier. I had to remove both of them to use the system. For example moving a window resulted in endless lagging copies of the window all over the screen, no sidebars etc. (And after removing it "GL vertex buffer object" is back to normal, "yes", if that information helps anyone understand my problem)

---

### Post by deadlylady on 2012-12-04
> **darkod said:**
> It might have worked for you (after several tries which another user might not handle as you did) and I mean no disrespect, but AMD instructions also say to create the .deb if installing the manual way.
So, I prefer to recommend the instructions of the manufacturer.

The quick way without creating debs, and what AMD also calls safest, is in the instructions too:
```
sudo apt-get install fglrx fglrx-amdcccle
```You won't have the latest Catalyst version, but it is quick and should be safe, and it still installs Catalyst.
Ok, this is what I got when entering your code:
> p@p-desktop:~/Desktop$ sudo apt-get install fglrx fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
fglrx-amdcccle is already the newest version.
fglrx-amdcccle set to manually installed.
The following packages were automatically installed and are no longer required:
  evolution-common libedataserverui-3.0-4 libevolution libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libidl-common libidl0:i386
  libmail-spf-perl libnetaddr-ip-perl libpst4 libytnef0 re2c spamassassin
  spamc thunderbird-locale-en thunderbird-locale-en-gb
  thunderbird-locale-en-us thunderbird-locale-zh-cn thunderbird-locale-zh-hans
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
p@p-desktop:~/Desktop$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string:  1.4 (2.1 Mesa 9.0)


I have been installing fglrx and debs both in terminal and in software center but obviously not the exact right ones. I will have a closer look at the page you linked and try to do it over again, thank you

---

### Post by deadlylady on 2012-12-04
> **element6 said:**
> Hummm..... Im trying to think back to my marathon weekend which got rid of the error.  The only other thing I did was install some libs per:



Then try installing the ATI driver:

 (or whatever driver you are trying to install)

Once again, the link: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx)

Let me know if it works.

EDIT: I did the install for 64bit.
No luck

---

### Post by darkod on 2012-12-04
Why does the OpenGL vendor string says VMWare? Are you talking about ubuntu inside a VM? I hope not, since inside the VM the video card usually would not be the same as the physical card.

With so many failed attempts, I would read carefully the Remove driver instructions and try to remove both fglrx and the debs versions you have installed earlier. Because right now you don't know what is used and what not.

One way to see if fglrx is used and the info, is running:
fglrxinfo

---

### Post by deadlylady on 2012-12-04
> **darkod said:**
> Why does the OpenGL vendor string says VMWare? Are you talking about ubuntu inside a VM? I hope not, since inside the VM the video card usually would not be the same as the physical card.

With so many failed attempts, I would read carefully the Remove driver instructions and try to remove both fglrx and the debs versions you have installed earlier. Because right now you don't know what is used and what not.

One way to see if fglrx is used and the info, is running:
fglrxinfo
I do not know what a VM/VMWare is unfortunately? :confused:

Yes this is exactly what I think I'm trying to do with the instructions on one of the pages you linked, trying to remove everything that has to do with the fglrx

Edit:

So now I've followed these steps:
>  **Problem: Need to purge -fglrx**

 Typically, the following manual commands will properly uninstall -fglrx: 

  sudo apt-get remove --purge xorg-driver-fglrx fglrx*   sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases   sudo dpkg-reconfigure xserver-xorgIf  you want desktop effects (compiz or KDE) you'll need the glx module  loaded. This will not work even after purging fglrx since a hanging libglx.so file is left around. Both fglrx and xserver-xorg-core provide this file so to replace it with the correct version you'll need to reinstall xserver-xorg-core as well. 

   sudo apt-get install --reinstall xserver-xorg-coreAnd feel ready to once more try and install the "amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.run"-file? I hope I have gotten it right this time finally, just gonna restart

Edit: That alone didn't do it unfortunately

---

### Post by deadlylady on 2012-12-04
p@p-desktop:~$ fglrxinfo
> fglrxinfo: command not foundbut on the RadeonDriver site i found this command: 
LIBGL_DEBUG=verbose glxinfo

which gave:
> name of display: :0
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/p/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_get_proc_address, 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string: 2.1 Mesa 9.0
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
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_ARB_depth_texture, GL_ARB_occlusion_query, 
    GL_ARB_shadow, GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, 
    GL_NV_fog_distance, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_draw_buffers, GL_ARB_fragment_program, GL_ARB_fragment_shader, 
    GL_ARB_shader_objects, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert, 
    GL_MESA_ycbcr_texture, GL_NV_primitive_restart, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_occlusion_query2, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_draw_instanced, GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_debug_output, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, GL_ARB_robustness, 
    GL_ARB_texture_storage, GL_ARB_invalidate_subdata

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x100 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x101 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x102 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x103 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x104 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x105 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x106 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x107 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x108 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x109 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x110 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x111 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x112 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x113 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x114 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x115 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x116 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x117 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x118 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x119 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x11d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x11e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x11f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x120 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x122 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x123 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x124 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x125 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x126 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x127 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x128 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x129 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x12f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x130 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x131 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x132 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x133 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x134 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x135 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x136 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x137 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x138 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x139 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x13b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x13c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x13d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x13e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x13f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x140 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x142 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x143 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x144 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x145 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x146 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x147 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x148 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x149 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x14a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x14b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x14c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x14d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x14e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x14f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x150 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x151 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x152 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x153 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x154 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x155 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x156 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x157 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x158 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x159 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x15a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x15b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x15c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x06f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x070 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x071 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x07e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x080 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x082 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x086 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x088 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x089 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x08a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x08c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x094 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x09d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x09e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x09f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0a0  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a4  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a6  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a7  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0a8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0aa  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ac  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ad  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ae  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b0  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b3  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b4  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b5  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b6  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b7  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0bb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0be 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0bf 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0ca 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0cb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0cc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0cd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0ce 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0cf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0d0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0da 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0db 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0dc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0dd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0de 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0df 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0e3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0e4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0e5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0e6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0e7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0e8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ea  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0eb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ec  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ed  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ee  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ef  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f4  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fa  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fe  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0ff  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow:guitar:

---

### Post by darkod on 2012-12-04
> **deadlylady said:**
> 

Edit:

So now I've followed these steps:
And feel ready to once more try and install the "amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.run"-file? I hope I have gotten it right this time finally, just gonna restart

Edit: That alone didn't do it unfortunately

Unfortunately, I don't know video driver installations in details. But what I have noticed is this:
You purged the fglrx to get rid of all traces. Did you also try to remove the driver you installed manually with the .run?

After purging fglrx, you still tried the .run without making .deb from it. Why???

The instructions of AMD and the wiki are clear:
1. As a short and safe way to install, install the fglrx and fglrx-amdcccle packages after you have purged fglrx.

2. If you prefer to install manually from the .run file to get the latest Catalyst, the procedure if first to make a .deb from the .run, and after that install that deb file.

You don't seem to have done neither of the above, or at least you didn't mention it. Installing fglrx seems as easy and recommended, so why don't you try it first?

But before trying it, you need to completely purge all drivers you have installed, including the fglrx and the driver installed by the .run.

And since this problem includes specific driver installation, not in general installation of the OS, you might have better help in the video section of the forum. There might be more specialized people to help there.

---

### Post by element6 on 2012-12-04
> **deadlylady said:**
> 

So now I've followed these steps:
And feel ready to once more try and install the "amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.run"-file? I hope I have gotten it right this time finally, just gonna restart

Edit: That alone didn't do it unfortunately

I see you are trying the beta drivers.  Are you able to install the released (12.10) successfully?  I successfully installed the 12.10 drivers using the "automatic" method in the AMD release notes.  Also review the System Recommendation section which outline required packages:

[http://www2.ati.com/relnotes/Catalyst_11.10_Linux_Installer.pdf](http://www2.ati.com/relnotes/Catalyst_11.10_Linux_Installer.pdf)

With the exception of needed to the header and such I mentioned earlier.  Maybe it is the 12.11 which is causing the issue?

Note sure.

---

### Post by deadlylady on 2012-12-05
> **darkod said:**
> Unfortunately, I don't know video driver installations in details. But what I have noticed is this:
You purged the fglrx to get rid of all traces. Did you also try to remove the driver you installed manually with the .run?

After purging fglrx, you still tried the .run without making .deb from it. Why???

The instructions of AMD and the wiki are clear:
1. As a short and safe way to install, install the fglrx and fglrx-amdcccle packages after you have purged fglrx.

2. If you prefer to install manually from the .run file to get the latest Catalyst, the procedure if first to make a .deb from the .run, and after that install that deb file.

You don't seem to have done neither of the above, or at least you didn't mention it. Installing fglrx seems as easy and recommended, so why don't you try it first?

But before trying it, you need to completely purge all drivers you have installed, including the fglrx and the driver installed by the .run.

And since this problem includes specific driver installation, not in general installation of the OS, you might have better help in the video section of the forum. There might be more specialized people to help there.
Thank you for your efforts. I'm sorry if I've been unclear but I've tried both these methods in different ways. The problem with the one purging and then installing the fglrx in the terminal is that it completely messes up my desktop surroundings rendering the operating system almost unusable.
The second method where I've tried purging everything according to for example [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") page's point 3.2 and then using a driver installer dosen't work because after selecting "install driver" and "continue" in the first picture this error-message appears:
> One or more tools required for installation cannot be found on the system.
Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
See /usr/share/ati/fglrx-install.log for more details. ...instead of the catalyst control center. 
However I HAVE managed to install it through unpacking the runfile into debs and then installing them instead as described [here]("http://forum.ubuntuusers.de/topic/amd-ati-treiber-12-10-12-11-ubuntu-12/2/?highlight=12.10+radeon+hd+#post-5009752"). This however also gives me a messed up desktop. I have gotten this result about 10 times now and sometimes it says "for testing only" in the right lower corner. To get my system back to a usable state (that is one with toolbars etc) I have to again delete the following packages:
ati binary driver and along with it
-fglrz-dev
-fglrz-amdcccle
So it seems that I've managed to install the package? Only that it leaves my system in worse shape than before. 

Thanks for the tip with the video section, will try to find something

---

### Post by darkod on 2012-12-05
As element6 noticed, you seem to be trying to install the Catalyst 12.11 Beta driver. Beta drivers are not final releases, so maybe that's where the problem is?

Have you tried downloading the 12.10 release which is final and stable, create the deb and install?

Also, you might need to remove xorg and let the driver recreate a new one (or manually you have to create it), but I'm not sure what's the best way to do that. Playing with xorg can leave the video really messed up and I have no experience with touching it.

---

### Post by deadlylady on 2012-12-07
> **darkod said:**
> As element6 noticed, you seem to be trying to install the Catalyst 12.11 Beta driver. Beta drivers are not final releases, so maybe that's where the problem is?

** Have you tried downloading the 12.10 release which is final and stable, create the deb and install?**

Also, you might need to remove xorg and let the driver recreate a new one (or manually you have to create it), but I'm not sure what's the best way to do that. Playing with xorg can leave the video really messed up and I have no experience with touching it.
**Yes, same problem with the 12.10.** Removing/creating the xorg has been a step of many of the guides I've worked with.

This is the latest guide I tried:
[http://www.upubuntu.com/2012/10/how-to-repair-failed-amd-catalyst.html](http://www.upubuntu.com/2012/10/how-to-repair-failed-amd-catalyst.html)
Which seemed to go well until this command:
sudo aticonfig --initial
which gave:
aticonfig: No supported adapters detected
After this I rebooted and ati binary driver was installed with the two usual packages and my desktop was messed up.

---

### Post by darkod on 2012-12-07
Did you check whether your card is supported? In the wiki posted earlier there was a link to see the unsupported cards.

In general, ATI cards should work by default with a driver/module called radeon. So, you might remove everything you tried, and see if by default it will work with that module. That driver has less features compared to fglrx but at least it should work stable with it. That might be one point to begin with.

If you can't make fglrx work you can consider continuing with radeon. And if your card is not supported than the fglrx driver won't work at all.

---

### Post by deadlylady on 2012-12-07
> **darkod said:**
> a)Did you check whether your card is supported? In the wiki posted earlier there was a link to see the unsupported cards.

b) In general, ATI cards should work by default with a driver/module called radeon. So, you might remove everything you tried, and see if by default it will work with that module. That driver has less features compared to fglrx but at least it should work stable with it. That might be one point to begin with.

If you can't make fglrx work you can consider continuing with radeon. And if your card is not supported than the fglrx driver won't work at all.
a) I'm having two problems with the page at the end of that link. For one I cannot choose radeon hd7770, it only goes up to "7500s", and secondly I can only seem to select windows operating system. I've tried googling and looking around the AMD page to get at another page for linux/Ubuntu.

b) where can I find a driver that is called radeon? Don't find anything googling and in software center only appears the same ati binary driver.

I found this thread:
[http://forums.gentoo.org/viewtopic-t-915244-start-0.html](http://forums.gentoo.org/viewtopic-t-915244-start-0.html)
with a user who also got the
> aticonfig --initial
aticonfig: No supported adapters detectedAnd now I'm looking at this page:
[http://en.gentoo-wiki.com/wiki/Fglrx#AMD_Radeon_HD_7700_Series](http://en.gentoo-wiki.com/wiki/Fglrx#AMD_Radeon_HD_7700_Series)
Maybe I can try it out?

---

### Post by darkod on 2012-12-07
This link, if it works, should open the Linux driver download page:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

The package/module radeon is included in ubuntu by default. I don't think you can add it (I don't know how it would be called either), but you shouldn't even need to add it.

For example, in my 12.04 I never installed any driver manually, and when I checked now it uses the radeon module. It does it by default. So, my idea was to remove all fglrx leftovers, reboot, and see if it tried to load radeon. You can list all loaded modules in ubuntu with:
lsmod

---

### Post by deadlylady on 2012-12-07
> **darkod said:**
> This link, if it works, should open the Linux driver download page:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

The package/module radeon is included in ubuntu by default. I don't think you can add it (I don't know how it would be called either), but you shouldn't even need to add it.

For example, in my 12.04 I never installed any driver manually, and when I checked now it uses the radeon module. It does it by default. So, my idea was to remove all fglrx leftovers, reboot, and see if it tried to load radeon. You can list all loaded modules in ubuntu with:
lsmod
Yes the driver you're linking I've found obviously. 

It lists "radeon" when I'm using the command you write hmmm... the unity3d didn't work from the beginning that's why I've installed all the drivers and packages? Do you think it might help if I installed Ubuntu 12.04 instead of 12.10?

---

### Post by darkod on 2012-12-07
The radeon module doesn't support 3D and other advanced options. But it is the default module that should work, at minimum.

It would be the same in 12.04 and 12.10, with radeon 3D won't work.

I checked on my desktop, if you open the Dash and start typing in the search line "Additional Drivers" and open the application, it should show the fglrx where you can activate it.

Doesn't it offer fglrx in your case? That should be the safest way to install it and use it.

On my desktop it shows it from day one, only I never activated it. I have a board with built-in HD3200.

---

### Post by deadlylady on 2012-12-11
> **darkod said:**
> The radeon module doesn't support 3D and other advanced options. But it is the default module that should work, at minimum.

It would be the same in 12.04 and 12.10, with radeon 3D won't work.

I checked on my desktop, if you open the Dash and start typing in the search line "Additional Drivers" and open the application, it should show the fglrx where you can activate it.

Doesn't it offer fglrx in your case? That should be the safest way to install it and use it.

On my desktop it shows it from day one, only I never activated it. I have a board with built-in HD3200.
Yeah the additional driver application dosen't seem to exist in 12.10 but I did search for the radeon driver you mentioned and found something like it although I can't find it again this moment. The fglrx only seems connected to the ati binary x.org driver.

I installed some updates today and the error-messages are fewer in ubuntu but still the two "no's" in unity 3d test

---

