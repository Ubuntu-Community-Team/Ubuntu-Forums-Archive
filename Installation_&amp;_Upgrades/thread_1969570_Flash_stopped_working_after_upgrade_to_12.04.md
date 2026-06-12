---
title: "Flash stopped working after upgrade to 12.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Russ_H on 2012-04-30
Hi,

    Flash has stopped working after upgrading to 12.04 LTS, flash does not work on youtube and more worryingly on BBC Iplayer. Installed flash aid on Mozilla, no different, reinstalled flash, again no different, Chrome tells me that it is installed already when I tried updating through Chrome, installed Opera, again no joy. Flash version is 11.2.202.233. HTML5 works fine on youtube. Any ideas anyone?

---

### Post by SJackson on 2012-04-30
Bumping for relevance.

---

### Post by Russ_H on 2012-05-01
> **Russ_H said:**
> Hi,

    Flash has stopped working after upgrading to 12.04 LTS, flash does not work on youtube and more worryingly on BBC Iplayer. Installed flash aid on Mozilla, no different, reinstalled flash, again no different, Chrome tells me that it is installed already when I tried updating through Chrome, installed Opera, again no joy. Flash version is 11.2.202.233. HTML5 works fine on youtube. Any ideas anyone?

It seems like quite a lot is not working, XBMC and Transmission will not start. XBMC has a crash log. WINE seems unaffected, run LTSPICE simulations OK.



################# LOG FILE ##################

&#65279;22:29:34 T:129586944  NOTICE: -----------------------------------------------------------------------
22:29:34 T:129586944  NOTICE: Starting XBMC (11.0 Git:Unknown), Platform: Linux (Ubuntu 12.04 LTS, 3.2.0-24-generic i686). Built on Apr 24 2012
22:29:34 T:129586944  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
22:29:34 T:129586944  NOTICE: special://xbmcbin/ is mapped to: /usr/lib/xbmc
22:29:34 T:129586944  NOTICE: special://masterprofile/ is mapped to: /home/russel/.xbmc/userdata
22:29:34 T:129586944  NOTICE: special://home/ is mapped to: /home/russel/.xbmc
22:29:34 T:129586944  NOTICE: special://temp/ is mapped to: /home/russel/.xbmc/temp
22:29:34 T:129586944  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
22:29:34 T:129586944  NOTICE: Local hostname: russel-laptop
22:29:34 T:129586944  NOTICE: Log File is located: /home/russel/.xbmc/temp/xbmc.log
22:29:34 T:129586944  NOTICE: -----------------------------------------------------------------------
22:29:34 T:129586944  NOTICE: Setup SDL
22:29:34 T:129586944  NOTICE: load settings...
22:29:34 T:129586944   ERROR: Unable to load libcrystalhd.so.3, reason: libcrystalhd.so.3: cannot open shared object file: No such file or directory
22:29:34 T:129586944  NOTICE: special://profile/ is mapped to: special://masterprofile/
22:29:34 T:129586944  NOTICE: loading special://masterprofile/guisettings.xml
22:29:34 T:129586944  NOTICE: Getting hardware information now...
22:29:34 T:129586944  NOTICE: Checking resolution 11
22:29:34 T:129586944  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
22:29:34 T:129586944  NOTICE: Loaded playercorefactory configuration
22:29:34 T:129586944  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
22:29:34 T:129586944  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
22:29:34 T:129586944  NOTICE: No settings file to load (special://xbmc/system/advancedsettings.xml)
22:29:34 T:129586944  NOTICE: No settings file to load (special://masterprofile/advancedsettings.xml)
22:29:34 T:129586944  NOTICE: Default DVD Player: dvdplayer
22:29:34 T:129586944  NOTICE: Default Video Player: dvdplayer
22:29:34 T:129586944  NOTICE: Default Audio Player: paplayer
22:29:34 T:129586944  NOTICE: Disabled debug logging due to GUI setting. Level 0.
22:29:34 T:129586944  NOTICE: Log level changed to 0
22:29:34 T:129586944  NOTICE: Loading media sources from special://masterprofile/sources.xml
22:29:34 T:129586944  NOTICE: Using visual 0x22
22:29:35 T:129586944  NOTICE: GL_VENDOR = Tungsten Graphics, Inc
22:29:35 T:129586944  NOTICE: GL_RENDERER = Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
22:29:35 T:129586944  NOTICE: GL_VERSION = 2.1 Mesa 8.0.2
22:29:35 T:129586944  NOTICE: GL_SHADING_LANGUAGE_VERSION = 1.20
22:29:35 T:129586944  NOTICE: GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_half_float_vertex GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness


############### END LOG FILE ################

############ END XBMC CRASH LOG #############

---

### Post by phillipmaloney on 2012-05-01
I'm on 11.10 and ran update manager tonight but did not upgrade to 12.04. 2 of the updates were flash plugin installer files. after finishing the updates i went to hulu.com to watch a movie and hulu said i didn't have the latest version of flash player and directed me to adobe's site. well it worked before i updated; I watched 2 movies on Monday. so just d/l flash player from adobe and open and install it with softwarecenter and you should be good to go.

---

### Post by Russ_H on 2012-05-01
> **phillipmaloney said:**
> I'm on 11.10 and ran update manager tonight but did not upgrade to 12.04. 2 of the updates were flash plugin installer files. after finishing the updates i went to hulu.com to watch a movie and hulu said i didn't have the latest version of flash player and directed me to adobe's site. well it worked before i updated; I watched 2 movies on Monday. so just d/l flash player from adobe and open and install it with softwarecenter and you should be good to go.

Tried a manual install and also the flash-aid for Mozilla, still no joy. If you right click over the blank bit where the video should be it gives a "video not loaded" and the flash version which is 11.2.202.235.

---

### Post by darkod on 2012-05-01
Few years back I had issues making 64bit flash plugin work. I managed to install it manually and always do it manually since then, even if the auto methods have improved.

Simply download it from the Adobe website, unpack the file. You need only the .so library.

Copy it to your /Home/.mozilla/firefox/plugins folder (I think that was the correct path, not on my ubuntu now), and that's it. If the plugins folder doesn't exist simply create it.

Much easier than depending on installers.

---

### Post by robert shearer on 2012-05-01
try here...
[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Russ_H on 2012-05-01
> **robert shearer said:**
> try here...
[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

No joy, still the same. Reports that 11.1.102.63 has been installed as per instructions but "movie not loaded" appears greyed out just above the version number as it did previously.

---

### Post by darkod on 2012-05-02
Did any of you tried adding the plugin as per post #6? I didn't see anyone that said he tried and failed to work.

It works for me.

---

### Post by Russ_H on 2012-05-02
> **Egeria said:**
> Well so far,12.04 adobe air was difficult to install, but sudo su and dragging and dropping the bin into the terminal worked, but cant install any apps, BBC iplayer desktop will not download, tried a radioplayer too; nothing, it seems to be confined to adobe air apps for me.
I thought I'd try wine and play-on Linux to see how it was effected and it crashes the explorer graphics so I removed it, screenlets tell me they've crashed but they are still there and working? I think the Ubuntu people should access the 6 month cycle of change 12.04 could have done with a bit more cooking  mostly a lot of the apps that make things bearable and are useful don’t work and are not supported. why adobe stopped supporting air in linux I cant imagine, they could have at least allowed and open sourced version.

I thought this was going to be a big leap forward, it is a leap, more a leap of faith in the Ubuntu people that they could get ..an LTS version right this time. I've got to say no they have not, far to much of what people use in the everyday is not working, its just not good enough, I may go back to 11.10 at least it worked or rather the apps I used in it worked which is really the important point. what’s the point in a desktop environment if all the apps you use on a daily basis don’t work? It does not matter how clever it is or how pretty it is, it has to work with the apps that you use or its useless.

If something does not come up PDQ I am going back to 10.04, this is a disaster, so much is just not functioning. I expected a few bugs but not on this scale, this is more like a pre beta from my perspective.

---

### Post by Russ_H on 2012-05-02
> **darkod said:**
> Did any of you tried adding the plugin as per post #6? I didn't see anyone that said he tried and failed to work.

It works for me.

Yes I did and it makes no difference.

---

### Post by SingingBush on 2012-05-02
I've found Flash to be buggy. I can start watching a video on youtube but eventually the controls at the bottom of the video are replicated all over the place. For some reason I also had a paused youtube video stuck in the top left of the screen which could only be seen on white space. eg, if i opened gedit and moved it up to the corner I could see it.

---

### Post by darkod on 2012-05-02
> **Russ_H said:**
> Yes I did and it makes no difference.

Did you remove all attempts and packages that didn't work? Unless you remove them first it will keep trying to use them so you will get the same message/failure.

You need to remove --purge them all.

---

### Post by darkod on 2012-05-02
OK, I just did a test in one virtual machine I have. It was installed brand new few days ago to test a LVM setup. It did not have flash or anything installed, just the regular updates.

As you can see on the first attachment, I opened [www.speedtest.net](www.speedtest.net) to show there is no flash installed. The message clearly says you need flash.

After that I downloaded the flash 11 file from adobe (the 32bit since the test machine is ubuntu 12.04 32bit). I extracted the .tar.gz.

I created a folder /home/username/.mozilla/plugins. The plugins folder does not exist in your home folder in .mozilla. I simply created it and copied the libflashplayer.so.

Close and open firefox. Voila, speedtest now works.

---

### Post by Russ_H on 2012-05-02
> **darkod said:**
> OK, I just did a test in one virtual machine I have. It was installed brand new few days ago to test a LVM setup. It did not have flash or anything installed, just the regular updates.

As you can see on the first attachment, I opened [www.speedtest.net](www.speedtest.net) to show there is no flash installed. The message clearly says you need flash.

After that I downloaded the flash 11 file from adobe (the 32bit since the test machine is ubuntu 12.04 32bit). I extracted the .tar.gz.

I created a folder /home/username/.mozilla/plugins. The plugins folder does not exist in your home folder in .mozilla. I simply created it and copied the libflashplayer.so.

Close and open firefox. Voila, speedtest now works.

The problem does not appear to there being no libflashplayer.so in the correct directory and of the correct version or previous version. When I try and run flash I get a grey screen. If I right click a box appears saying "movie not loaded" underneath is the version of flash, which changes when I change versions.

---

### Post by graham.s on 2013-04-07
I think I may have found a fix - similar to darkod. Worked for me. I had a completely clean install of 12.04 Precise on a oldish machine. All fine except for Flash not working in Firefox at all - no matter what I tried with FlashAid, etc. Finally solved like this:
1. Used Synaptic to completely uninstall flashplugin-installer which had been installed from Ubuntu repositories (and also, in my case, the GTK Flash setting frontend).
2. Checked that there was now no libflashplayer.so in [root] /usr/lib/mozilla/plugins.
3. Downloaded an archived version of Flash - I chose to use the last of the 10.3 versions.
4. Used Archive Manager tpo extract just the libflashplayer.so file and put it in /home/[myuser]
5. Copied the file to the plugins folder using
   >  sudo cp /home/[myuser]/libflashplayer.so /usr/lib/mozilla/plugins 
6. Started Firfox and tested iPlayer and YouTube - both now worked first time. Rebooted and rechecked - everything fine!

Hope that helps

Graham

---

### Post by silbar on 2013-07-18
Greetings,

darkod suggests putting latest libflashplayer.so in .mozilla/firefox/plugins.  Didn't work for me -- when I try loading separate pages concurrently with their flash ads, I get many crashes.

RRS

---

### Post by silbar on 2013-07-18
Having just seen graham.s's posting just before the one before this (by me), I also tried his suggestion of putting the libflashplayer.so in /usr/lib/mozilla/plugins.  Not a solution (for me) -- still get multiple crashes on multiple concurrent pages.

By the way, my work-around for this problem is to not try opening more than one page with flash video at a time.

RRS

---

