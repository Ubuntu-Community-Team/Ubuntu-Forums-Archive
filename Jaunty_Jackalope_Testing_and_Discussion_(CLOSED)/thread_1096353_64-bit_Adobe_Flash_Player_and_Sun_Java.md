---
title: "64-bit Adobe Flash Player and Sun Java"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-03-14
Curious as to whether or not 9.04 will include in the repositories the 64-bit versions of Sun Java and Adobe Flash Player.

I know the flash player is an alpha right now, not sure if that means it won't be included or not.

Anyone currently using 9.04 that can tell me if the native 64-bit versions of these are available to install using 9.04 repos?

---

### Post by pferraro on 2009-03-14
> **novafluxx said:**
> Curious as to whether or not 9.04 will include in the repositories the 64-bit versions of Sun Java and Adobe Flash Player.

I know the flash player is an alpha right now, not sure if that means it won't be included or not.

Anyone currently using 9.04 that can tell me if the native 64-bit versions of these are available to install using 9.04 repos?

Java, yes.
Flash, no - but its easy enough to install (download and copy a single file to the right place).

---

### Post by novafluxx on 2009-03-14
Thank you! Thats good to know! I think I'm going to stick with 32-bit for now though, at least until wine is 64-bit (I'm a gamer!)

I'm running 8.10 64-bit right now, but I think I'm going to reinstall 32-bit just to make sure everything is compatible :-)

Yes I'm using the Adobe Flash plugin now, its very easy to "install" just by cp the file :-)

---

### Post by Nullack on 2009-03-14
64bit flash misses functions in the 32 bit version, most importantly OpenGL acceleration is only in 32 bit

---

### Post by zika on 2009-03-15
> **Nullack said:**
> 64bit flash misses functions in the 32 bit version, most importantly OpenGL acceleration is only in 32 bit
could You please elaborate on this.

---

### Post by Nullack on 2009-03-15
There is no OpenGL acceleration for flash content on the 64bit flash version. Only the 32 bit version supports it. Additionally, only the 32 bit version with Compiz off, because Linux has a broken video architecture (work is underway to fix it).

The repos install the 32 bit version by default on 64 bit platforms, which is a wise decision in my book.

---

### Post by zika on 2009-03-15
> **Nullack said:**
> There is no OpenGL acceleration for flash content on the 64bit flash version. Only the 32 bit version supports it. Additionally, only the 32 bit version with Compiz off, because Linux has a broken video architecture (work is underway to fix it).
The repos install the 32 bit version by default on 64 bit platforms, which is a wise decision in my book.
so You say that I would be better off with flashplugin-nonfree than with 64-bit plugin from Adobe download page. I think I even do not have any video acceleration on my ATI HD 3650 and Jaunty ... ;)
```
zika@zika-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.3
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
```

so, You still advise me to switch to flashplugin-nonfree?

---

### Post by Nullack on 2009-03-15
Your free to do as you please :) For me, I like OpenGL acceleration. It could be argued that the 64bit version is less mature than the 32 bit one, but then again, when I have run tests on the 64 bit version I have encountered any specific functional problems with it - albeit within the limitations of what that version offers.

---

### Post by asimon on 2009-03-15
I used the 64 bit flash a couple of days and think it's not ready for production yet. I experienced a lot of freezes where I had to kill -9 firefox.

---

### Post by other guy on 2009-03-15
> **asimon said:**
> I used the 64 bit flash a couple of days and think it's not ready for production yet. I experienced a lot of freezes where I had to kill -9 firefox.

Under older variants of Ubuntu, like 8.10 and earlier.. I used the 64bit Flash without any issue. Actually it was more stable and did not bog down browsing. Seems the 32bit wrapper never liked me much. I liked the 64bit flash since it worked great for me.

Jaunty, with the Firefox and 64bit is like the issue before. Freezing and random issues when flash comes into the browser. Seems to be getting worse now as I keep using it.

Wonder if I need to file a bug report.

---

### Post by asimon on 2009-03-15
> **other guy said:**
> Wonder if I need to file a bug report.
Only Adobe can fix it.

---

### Post by other guy on 2009-03-15
Like before.. Why  I never filed on it. I could be Moz or Adobe.

I used to have the native 32bit freezing issues also.

---

### Post by Arathorn on 2009-03-15
> **novafluxx said:**
> Thank you! Thats good to know! I think I'm going to stick with 32-bit for now though, at least until wine is 64-bit (I'm a gamer!)
Maybe I'm misunderstanding you, but Wine compiled for x64 systems runs 32 bit Windows programs perfectly well. It doesn't support 64 bit Windows programs yet, but for gaming that shouldn't be a problem.

---

### Post by novafluxx on 2009-03-16
Remember the Adobe Flash plug-in is still in alpha state...of course its not production ready yet!!

Let them get it out of the testing/development stage before we criticize. ;)

---

### Post by Nullack on 2009-03-16
Surely adobe have some method for reporting bugs?

Additionally, how are you all not certain that some related library or other infrastructure was upgraded in Jaunty, causing this regression? That could help the path to fixing it.

---

### Post by other guy on 2009-03-16
> **Nullack said:**
> Surely adobe have some method for reporting bugs?

Additionally, how are you all not certain that some related library or other infrastructure was upgraded in Jaunty, causing this regression? That could help the path to fixing it.

I wish I could be sure what was the exact culprit. I am not having the hard freeze like flash used to give. It still does make Firefox and Opera freeze up.

It just started too. Before flash heavy sites were stable and just worked. The odd here and there due to poor design / older sites or what not. I did encounter that, but did not blame anything but the site.
Now I get freezing on video sites like liveleak and youtube mainly. Few other flv sites, but them I hit the most often. It could be some obscure regression. I am unsure what it could be actually. At this point, all I know it is freezing alot when going on major flv sites.

I would be glad to pitch in and help find out what is wrong, but do not know where to start. Even if this is just a Jaunty issue or an Adobe issue. It could even be a Firefox issue. As before, it seemed no one got it nailed down to which one was doing it. I can probably think along the lines, maybe pulseaudio is helping it crash. I do not know for sure or have proof. 

There is a number of unresolved bug files for the adobe flash 10. I checked the issue navigator.
[https://bugs.adobe.com/jira/secure/IssueNavigator.jspa?reset=true&&type=1&pid=10080&sorter/field=issuekey&sorter/order=DESC](https://bugs.adobe.com/jira/secure/IssueNavigator.jspa?reset=true&&type=1&pid=10080&sorter/field=issuekey&sorter/order=DESC)

In the spirit of the topic. As far as I can tell java is in the Juanty repos and does not use any nswrapper when going 64bit.

---

### Post by zorkerz on 2009-03-25
Arathor you are right. Wine not supporting 64-bit means it cannot run 64-bit windows applications. Wine runs 32-bit applications fine on 32 and 64 bit ubuntu in my experience.

---

### Post by ktp on 2009-03-25
I have been using flash 64 for while now and not seen much issues.  Seems to be really stable for my use.

---

### Post by syko21 on 2009-03-25
Try temporarily switching to alsa from pulseaudio and see if you still have stability issues. Pulseaudio has massive cpu spikes during some flash games and videos for me.

---

### Post by novafluxx on 2009-03-26
> **ktp said:**
> I have been using flash 64 for while now and not seen much issues.  Seems to be really stable for my use.

Same here, although it is an alpha, and be definition its not full featured yet. I'm going to assume Adobe will make sure it has all the features the 32-bit plugin does before designating it a beta release, then we'll test that one :)

I've had no issues with it thus far. I'm also using the refresh from February, not the one from December.

---

### Post by a3qp on 2009-03-27
I was using a flash editor (flashdigger plus) in windows. When I switched to Ubuntu, I mainly had to install virtualbox just for  that software (I still don't know any flash editor in Ubuntu, are there?).

Today, I installed wine, and then ran the flash editor, but it pops up a message that says:
"This software requires Adobe Flash Player ActiveX(tm), which is not installed on your computer. Please install it first.".

I installed flashplugin-nonfree, from the Synaptic menus, and then I also realized that I had installed  Macromedia Flash Plugin in the Add/Remove Applications menu.

However, the software continues saying: "This software requires Adobe Flash Player ActiveX(tm), which is not installed on your computer. Please install it first."

What can I do?

I have amd64, Jauny (9.04).

Thanks

---

### Post by Mutiny32 on 2009-03-27
> **Nullack said:**
> Your free to do as you please :) For me, I like OpenGL acceleration. It could be argued that the 64bit version is less mature than the 32 bit one, but then again, when I have run tests on the 64 bit version I have encountered any specific functional problems with it - albeit within the limitations of what that version offers.
I'd rather have a flash player that works at all. Nspluginwrapper crashes are more common than flash actually working. And I think the Feb refresh supports hardware acceleration.

---

### Post by Reiger on 2009-03-27
> **a3qp said:**
> I was using a flash editor (flashdigger plus) in windows. When I switched to Ubuntu, I mainly had to install virtualbox just for  that software (I still don't know any flash editor in Ubuntu, are there?).

Today, I installed wine, and then ran the flash editor, but it pops up a message that says:
"This software requires Adobe Flash Player ActiveX(tm), which is not installed on your computer. Please install it first.".

I installed flashplugin-nonfree, from the Synaptic menus, and then I also realized that I had installed  Macromedia Flash Plugin in the Add/Remove Applications menu.

However, the software continues saying: "This software requires Adobe Flash Player ActiveX(tm), which is not installed on your computer. Please install it first."

What can I do?

I have amd64, Jauny (9.04).

Thanks

You have downloaded a **Windows 32bit** installer from Adobe and installed from that?

---

### Post by other guy on 2009-03-27
> **Mutiny32 said:**
> I'd rather have a flash player that works at all. Nspluginwrapper crashes are more common than flash actually working. And I think the Feb refresh supports hardware acceleration.


I also got tired of the npveiwer.bin crashing. Plus it is really easy to just drop the libflashplayer.so in the .mozilla plug-in folder. Once I found out it was that easy. I used that. Plus the wrapper made my browser slow in some sites and ate a lot of CPU time. 

I changed out the libflashplayer.so file and I am back to a reasonable flash experience again.

---

### Post by tjeremiah on 2009-03-27
still experiencing major screen tearing with flash video. I havent solved that problem with 8.10.

---

### Post by Nullack on 2009-03-27
> **Mutiny32 said:**
> I'd rather have a flash player that works at all. Nspluginwrapper crashes are more common than flash actually working. And I think the Feb refresh supports hardware acceleration.

Id be delighted if the 64bit has added opengl acceleration - got a source for that info?

---

### Post by taavikko on 2009-03-27
> **Nullack said:**
> Id be delighted if the 64bit has added opengl acceleration - got a source for that info?

There you go mate, [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
That should clear some issues...

At least on my weary eyes there's stated that some is pushed to GPU.

I've been running this beta, on my main comp for a while. It definitely feels snappier than the one available via flashplugin-nonfree

But then again, I might be wrong :)

---

### Post by novafluxx on 2009-03-29
Just tried to install Java from add/remove programs...looks like even though im running 64-bit, it installs the 32-bit version of Sun Java.

Come on now, whats up with that? Sun Java 6 Update 12 and now Update 13 both are 64-bit compatible now...why are they not included in the Jaunty repos?

Part of marketing of Ubunutu is that all these programs and stuff are just a few clicks away...well yeah, but they also need to uh...work maybe.

Guess I'll be installing it manually, just like I did in 8.10

---

### Post by novafluxx on 2009-03-30
Anyone else discover this?

---

### Post by zika on 2009-03-30
> **novafluxx said:**
> Anyone else discover this?
are You sure it is 32-bit?
(thi is after today's upgrade but I think even for subversion 12 was the same)
```
~$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)
```

---

### Post by a3qp on 2009-03-30
> **Reiger said:**
> You have downloaded a **Windows 32bit** installer from Adobe and installed from that?

I downloaded: Adobe Flash Player, for windows vista/xp/2003, for Firefox, I installed using Wine, but still the same problem.
The software says: "This software requires Adobe Flash Player ActiveX(tm), which is not installed on your computer. Please install it first.".

any idea?

---

### Post by zorkerz on 2009-03-30
Ive never heard of anyone trying to use a windows flash player in linux. I think that will just lead to more problems.

---

### Post by a3qp on 2009-03-30
And so, do you know any flash editor in Linux?
This is one of the mainissues that keeps me running virtualbox (winXP) on Ubuntu.

Thanks,

---

### Post by zorkerz on 2009-03-30
Oh flash editor. I have no idea. Have not done any of that for years and at that point I was on windows.

---

### Post by novafluxx on 2009-04-01
> **zika said:**
> are You sure it is 32-bit?
(thi is after today's upgrade but I think even for subversion 12 was the same)
```
~$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)
```

Well all I know is after installing it from the repo's using apt-get, I tried to test it in Firefox, and it offered me the IcedTea plugins saying it was required to view content on that page.

---

### Post by novafluxx on 2009-04-02
I discovered the issue...

When I installed Java 6 Update 13 from the repos...it installed the 64 bit version, correct, however it doesn't install the PLUGIN!:lolflag:

Also, when you attempt to view a java applet in Firefox, the Sun plugin for Java is not offered in the list.

I used synaptic and installed the plugin, all works well! Yes!

---

