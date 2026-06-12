---
title: "Can't Install Ubuntu with Ati Radeon X1950 Pro AGP 512 Mo"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by bibendum on 2008-02-06
Hi
I'm trying to install Ubuntu with CD Desktop on my computer, but i can't do it !!! 
All the time, even in Safe VGA Mode, i get the message : Xserver has reboot 6 times in 90 secondes.
Probably due to my ATI Radeon X1950 Pro AGP 512 Mo.
How to install Ubuntu with CD Desktop with my X1950 Pro ?
I'm newbie and really need detailled help to try Ubuntu  ;-)
Thanks a lot for your help.

---

### Post by Rocket2DMn on 2008-02-06
You will probably need to use the alternate install cd which is a text based installer without a live session - it's intuitive and works very well.  You can download it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom for Alternate cd.
After you install, you will probably want the restricted ati drivers - [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by bibendum on 2008-02-07
Hi Rocket2DMn

I've tried Alternate CD, without any succes :(

I will try again, perhaps i forget something, i will come back to inform you.

Thanks

---

### Post by bibendum on 2008-02-07
Hi

Nothing to do, after 6 install, i can't start Ubuntu with my ATI card, i will go back to Windows  :(

---

### Post by Rocket2DMn on 2008-02-07
After you have it installed (even if you can't get to the GUI yet), we can run the X-server reconfiguration program if you're still interested.

---

### Post by bibendum on 2008-02-07
> **Rocket2DMn said:**
> After you have it installed (even if you can't get to the GUI yet), we can run the X-server reconfiguration program if you're still interested.

Of course i'm still interrested !!! 

At this time, i'm using Ubuntu in recovery mode and using "startx" 

Ubuntu ask me to enable restricted drivers for mu ATI card, if i do that, i won't can be see display again !!! 

What must i do now ? 

sudo apt-get install linux-restricted-modules-generic restricted-manager-kde ? 

And install new ATI drivers ? 

Thanks

---

### Post by Rocket2DMn on 2008-02-07
reboot into the recover kernel from GRUB and run
```
dpkg-reconfigure xserver-xorg
```
You will be asked a bunch of questions about your hardware, do your best to answer.  At the driver questions, select "vesa", and at the resolutions page, use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less.  When it's finished, reboot into the regular kernel
```
reboot
```
Once in the GUI you can install the restricted ati drivers - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Let me know how that works out, we may need to install the drivers via terminal before logging into X.

---

### Post by bibendum on 2008-02-07
Hi 

I 've done all instructions found in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

After reboot, blank screen, in all mode :(

I will try with your info, i come back early :)

---

### Post by bibendum on 2008-02-07
Hi 

Nothing better :(

After reconfigure xserver, starting in regular kernel and Spash Screen Ubuntu is in high resolution, and i get a message : xserver was reboot 6 times in 90 seconds, please wait 2 min before to try again.

---

### Post by Rocket2DMn on 2008-02-07
Well, it seems a lot of other users are having problems with the AGP version of this card as well, and after consulting some other experienced users, they don't have any suggestions either.  So, you have 2 options really.
1) Wait awhile until your card has better support in Ubuntu (I think your card is really new, and hardware support lags a bit in linux)
2) Buy a different card that does have good support in linux.  NVidia tends to have the best support, but if you're a hardcore ATi fan, there are many cards that do work.

Sorry we weren't able to fix your problem :(

---

### Post by bibendum on 2008-02-08
Hi 
My card is not so really new, December 2006.
Is it possible to start Ubuntu in low resolution, because now, i can't get GUI, in all mode, i have blank screen and can't test anything else.
I just can have terminal in recovery mode.
Thanks

---

### Post by Rocket2DMn on 2008-02-08
You can do the reconfiguration again and select the "vesa" driver, this is like the fallback one.  You may actually just be able to edit the file directly to do that
CTRL+ALT+F1 to tty and login, then
```
sudo nano /etc/X11/xorg.conf
```
and scroll down to the "driver" the "Device" section.  Change from "fglrx" or "ati" or "radeon" to "vesa".  Then restart kde
```
sudo /etc/init.d/kdm restart
```
If manual edit doesn't work, just reconfigure and select vesa.

---

### Post by bibendum on 2008-02-08
Hi
That's better, i,m now at 1600x1200 with Vesa Generic driver,
fglrx was in xorg.conf, remplaced like you tell me with vesa
Must i wait after better support or can i try something else ? 
Thanks

---

### Post by Rocket2DMn on 2008-02-08
I think you better stick with that works, I'm not sure if more support will come for the AGP version of your card.  Is it now at the best resolution?  You probably don't have 3d acceleration, but if it works...

---

### Post by bibendum on 2008-02-08
Yes, i don't have 3D accelleration :(

So i think i will go back to windows :(

---

### Post by bibendum on 2008-02-08
Something i don't understand : when i start Ubunto in recovery mode and i type "startx", i can get GUI in 1600x1200.
When i start Ubuntu in normal mode, i can't get any display.
Why ?

---

### Post by Rocket2DMn on 2008-02-08
I thought you said you had it working with vesa, just no 3d accel.  Do you have 3d accel when you do it recovery mode?  Run
```
glxgears -info
```
And look at your FPS - if you are getting a few hundred or more, then you probably have 3d accel.

---

### Post by bibendum on 2008-02-08
Hi 

Very good news, after so many search, i found information,  my Radeon is now activated :):):)

> GL_RENDERER   = Radeon X1950 Series
GL_VERSION    = 2.0.6473 (8.37.6)
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_pixel_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ARB_draw_buffers GL_ATI_draw_buffers GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_separate_stencil GL_ATI_shader_texture_lod GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
353 frames in 5.0 seconds = 70.563 FPS
339 frames in 5.0 seconds = 67.591 FPS
375 frames in 5.0 seconds = 75.000 FPS
374 frames in 5.0 seconds = 74.800 FPS
375 frames in 5.0 seconds = 74.939 FPS

But still have problem with 3D.

When i try to install GLX Server to use 3D effect, display is very very slow.
Without GLX Server, i get this message : The Composite Extension Is Not Avaible
With GLX, i get message about something can't be load.

---

### Post by Rocket2DMn on 2008-02-08
Good to hear.  You can backup for xorg.conf file and continue fiddling if you want.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Otherwise just be happy it works :)

---

### Post by bibendum on 2008-02-08
Thanks for your help Rocket2DMn, you put me in the good way :)

I'm still looking information to activate 3D Effect in my desktop :confused:

---

### Post by thomasbaker on 2008-02-09
Well I have the same card, and the same issues can you tell us what you did to fix it please!!!

Thanks

---

### Post by bibendum on 2008-02-09
Hi

It's seem that 3D features can't be enabled with my ATI product. 

From ATI Web Site : 

> 737-26907: Unsupported Features with ATI Linux Drivers

    The information in this article applies to the following configuration(s):

        * AIGLX
        * Beryl
        * Compiz
        * MythTV
        * TV TIME

    Currently, the following features are not supported with ATI Linux drivers.

        * AIGLX, Beryl, Compiz, MythTV, TV TIME

So no Compiz and his beautifull 3D Cube display :(

thomasbaker, do you still need help ?

---

### Post by thomasbaker on 2008-02-09
yes I do, I've been using windows, but would like to go back to ubuntu.  I will upgrade my pc later to a PCIe but thats a few months away.

So any help would be awesome.

thomas

---

### Post by bibendum on 2008-02-09
Hi

Let me some day because i'm still fighting to activate 3D !!!

---

