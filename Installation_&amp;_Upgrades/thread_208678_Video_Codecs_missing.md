---
title: "Video Codecs missing?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by HackMaster on 2006-07-03
I just installed ubuntu in a dual boot configuration with my windows partition. I absolutely love ubuntu, but one issue has me stuck, and i have one other question. My big issue first.

Whenever i attempt to play a video, using Todem, it complains. Here is the exact error message it gives:
> Todem could not play 'file:///media/storage/xmenthelaststand_h1080p.mov'.

You do not have a decoder installed to handle this file.
You might need to install the necessary plugins.

This happens with every single video, from xvid, to WMV. is there a package i need to grab somewhere?

----
My next question is a musing, I have a high-end graphics card in my computer here (nVidia GeForce Go 6800, reported as "NV41.8". Whenever my nice screensaver comes on, the computer grinds to a halt, and the screensaver gets quite ugly. Most of the screensavers, when previewed in the "Screensaver Preference" window, cause a significant hit on my CPU usage, often completly consuming a whole CPU (P4 3.4GHz HyperThreaded). Does this mean that the graphics work is being done on the CPU, when it should be computed on the GPU? or is this just how linux works?

Well, while i am on a roll here, i guess I will ask a final question about audio. My audio works great in normal 2 channel mode, but I cannot find a way to change the modes. In windows, i could enable up to 7.1 (Intel Integreated 7,1 HD audio). It achieved this by turning the MIC-IN port into the Rear Channel Out, and so on. Is such an thing possible in linux? Audio is recognized as: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller.

Thanks!

---

### Post by evilghost on 2006-07-03
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

---

### Post by -deadcats on 2006-07-03
For a newbie, I'd recommend something like Automatix (among others). Takes care of a lot of the chores you're gonna need to do.

regards,
-dc

---

### Post by HackMaster on 2006-07-04
@evilghost
The first two packages, gstreamer0.10-gl and  gstreamer0.10-ffmpeg, registered as not existing. > sudo apt-get install gstreamer0.10-ffmpeg
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-ffmpeg has no installation candidate

the "good" entries were already installed, and the bad/ugly ones could not be found.

@-deadcats: I have read much about Automatix, but it will not run. I type "automatix" into a terminal window, but it says that the command is not found.

Thanks for the quick replys guys!

---

### Post by evilghost on 2006-07-04
Try 'gstreamer0.8-ffmpeg' instead, I just checked my dapper system and that's what I have installed.

---

### Post by Jagot on 2006-07-04
[QUOTE=HackMaster]The first two packages, gstreamer0.10-gl and  gstreamer0.10-ffmpeg, registered as not existing. 
the "good" entries were already installed, and the bad/ugly ones could not be found.[/QUOTE]

Yes, they do exist - they are in the universe repo, so I'm assuming you have not enabled it:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by lordlollo on 2006-07-04
You could also give a chance to EasyUbuntu...

---

### Post by mstlyevil on 2006-07-04
[QUOTE=HackMaster]@evilghost
The first two packages, gstreamer0.10-gl and  gstreamer0.10-ffmpeg, registered as not existing. 
the "good" entries were already installed, and the bad/ugly ones could not be found.

@-deadcats: I have read much about Automatix, but it will not run. I type "automatix" into a terminal window, but it says that the command is not found.

Thanks for the quick replys guys![/QUOTE]

Which version of Automatix are you using? I need to know this because I know how you can fix it but I need the exact version to be able to help you.

---

### Post by HackMaster on 2006-07-05
@jagot:
You were correct, there were a couple of repositories that were not enabled. I enabled them, and installed as many codecs as i could see that related to video/audio. There are a bunch. Most videos work, but Quicktime and WMV do not. I know they are not Closed Source, so the support might be lackluster, but are there any codecs out there that will support them? 

@mstlyevil: I do not have, as far as i can tell, Automatix installed. I tried to install it, by running "wget http://beerorkid.com/arnieboy/automatix_6.1_i386.deb", but the URL reported a 404. should Automatix be installed by default?

---

### Post by mstlyevil on 2006-07-05
[QUOTE=HackMaster]@jagot:
You were correct, there were a couple of repositories that were not enabled. I enabled them, and installed as many codecs as i could see that related to video/audio. There are a bunch. Most videos work, but Quicktime and WMV do not. I know they are not Closed Source, so the support might be lackluster, but are there any codecs out there that will support them? 

@mstlyevil: I do not have, as far as i can tell, Automatix installed. I tried to install it, by running "wget http://beerorkid.com/arnieboy/automatix_6.1_i386.deb", but the URL reported a 404. should Automatix be installed by default?[/QUOTE]

6.1 is a outdated package that has been removed. Here is the thread for how to get the current packages.

[http://ubuntuforums.org/showthread.php?t=190025]("http://ubuntuforums.org/showthread.php?t=190025")

---

### Post by beausimon on 2006-07-05
Which is better? Easyubuntu or Automatix?

---

### Post by mstlyevil on 2006-07-05
[QUOTE=beausimon]Which is better? Easyubuntu or Automatix?[/QUOTE]

Depends on what you want. EasyUbuntu does not have as many selections as Automatix and is harder to install. But neither one is better than the other, just different.

I would of course recommend Automatix since I am the assistant team lead of the project but check them both out and see which one you would prefer.

---

### Post by HackMaster on 2006-07-05
that works perfectly! Thanks man. You and your team have made an amazing utility.

It also installed a tool called "Windows Wireless Drivers". does this use windows-based drivers to use the wireless card? Mine is an Atheros, and is detected. It also finds my wireless networks, but it has a signal strength of 0%. Is that a driver problem?

Also, your package installed some nVidia drivers, but the fancy screen savers still consume lots of CPU power. Is that the best it will be?


Video/Audio Codecs: Fixed!!
Intel HD audio out: multi-channel not working.
nVidia GPU not taking load from CPU: not fixed.

Edit: one more thing. I noticed that audio in flash items (eg youtube, google video) does not play. Is there a fix for this?

---

### Post by evilghost on 2006-07-05
[QUOTE=HackMaster]that works perfectly! Thanks man. You and your team have made an amazing utility.

It also installed a tool called "Windows Wireless Drivers". does this use windows-based drivers to use the wireless card? Mine is an Atheros, and is detected. It also finds my wireless networks, but it has a signal strength of 0%. Is that a driver problem?

Also, your package installed some nVidia drivers, but the fancy screen savers still consume lots of CPU power. Is that the best it will be?


Video/Audio Codecs: Fixed!!
Intel HD audio out: multi-channel not working.
nVidia GPU not taking load from CPU: not fixed.

Edit: one more thing. I noticed that audio in flash items (eg youtube, google video) does not play. Is there a fix for this?[/QUOTE]

Post the output of the first page of:

```
glxinfo|more
```

---

### Post by HackMaster on 2006-07-06
```
michael@alienwareubuntu:~$ glxinfo|more
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6800/PCI/SSE2
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query,
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float,
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range,
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_NV_vertex_program3,
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3

```


And yet another problem. I get a notification about a new update, so i open the update manager, and the window manager crashes. My screen dies for a couple of seconds, and then the nVidia image appears, then i am prompted to logon. is this related to my install of all these packages from automatix? I have read that automatix conflicts with the update manager, but i understood it to mean that automatix will not run when the update manager is running, not to kill gnome when the update manager is run. I would test out other apps, but i dont want to lose this message.

---

### Post by mstlyevil on 2006-07-06
[QUOTE=HackMaster]```
michael@alienwareubuntu:~$ glxinfo|more
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6800/PCI/SSE2
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query,
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float,
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range,
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_NV_vertex_program3,
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3

```


And yet another problem. I get a notification about a new update, so i open the update manager, and the window manager crashes. My screen dies for a couple of seconds, and then the nVidia image appears, then i am prompted to logon. is this related to my install of all these packages from automatix? I have read that automatix conflicts with the update manager, but i understood it to mean that automatix will not run when the update manager is running, not to kill gnome when the update manager is run. I would test out other apps, but i dont want to lose this message.[/QUOTE]

No the crash is unrelated to Automatix. You have a serious problem in the update manager. Try updating from the terminal and see what happens.

Also could you post your /etc/X11/xorg.conf file so we can see if it is properly configured for Nvidia? This may be the problem with the Nvidia drivers.

---

### Post by HackMaster on 2006-07-06
/etc/X11/xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV41.8 [GeForce Go 6800]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41.8 [GeForce Go 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Thanks very much for your help, mstlyevil! I know i can always depend on the linux community!

Edit: just so you know a bit better, the window opens, it does some thinking, then it loads up the updates that need to be installed. it looks fine for about one second, then the window manager crashes. i can see about 3 packages that need to be updated.

---

