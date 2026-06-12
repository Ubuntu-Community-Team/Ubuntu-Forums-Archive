---
title: "Getting direct rendering with Gallium3d"
date: 2008-12-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by STEVE555 on 2008-12-26
Hi everyone,
           I have a problem.I'm currently using the latest nouveau drivers from the git repository, using this howto:[http:////nouveau.freedesktop.org/wiki/InstallNouveau]("http:////nouveau.freedesktop.org/wiki/InstallNouveau")and they're working fine.However I found them a bit a bit slow when I wanted to play Vegastrike since I soon found out I couldn't run OpenGL applications with them.So I decided to have a go at trying out the Gallium3d drivers from the git repository.

I used this howto:[http://nouveau.freedesktop.org/wiki/GalliumHowto]("http://nouveau.freedesktop.org/wiki/GalliumHowto")
(I changed git clone git://anongit.freedesktop.org/git/nouveau/mesa to
git clone git://anongit.freedesktop.org/git/mesa/mesa)and git checkout origin/gallium-0.1 to git checkout origin/gallium-0.2 to get the latest files.

I had compiled the code and installed the various files to their locations.However,when I run glxinfo,it tells me that direct rendering isn't switched on.I get this output:I have put it in glxinfo.txt.I'm running Kubuntu Jaunty Jackalope Alpha 2,my Graphics Card is a Nvidia Geforce 6800 GT with 256Mb of memory.My monitor is a ADI G1000 CRT.I'll put the other relevant files below this post.

Regards,
       STEVE555

---

### Post by RAOF on 2008-12-26
3D is aggressively unsupported; the developers know it's incomplete and don't want to hear when it doesn't work.

That out of the way, your nv4x is currently in the best-supported category.  You haven't done things the way I would have; I don't install the new mesa system-wide.

The really useful output would be from running
```

LIBGL_DEBUG="verbose" glxinfo

```
as it suggests.  It looks like it's using the nouveau 3d driver, anyway.

Oh, and AIGLX is not supported (except on the -ng branches) as far as I'm aware; disabling that might be a winner.

---

### Post by STEVE555 on 2008-12-27
Hi RAOF,
       I've done a LIBGL_DEBUG="verbose" glxinfo attached to this post.

Regards,
       STEVE555

---

### Post by STEVE555 on 2008-12-27
Hi RAOF,
       Here's an update,
I managed to get direct rendering at last!:),here's what I did:

I was looking at the output LIBGL_DEBUG="verbose" glxinfo was giving me.
I noticed that nouveau was looking for nouveau_dri.so and swrast_dri.so in
/usr/local/lib/dri,but when I looked in /usr/local/lib with dolphin,the dri folder wasn't there.

So I created the folder celled dri in there,and put nouveau_dri.so and swraster_dri.so into the folder.

I then ran sudo updatedb and re-booted,and hey presto! direct rendering is now working!
```
root@mernivia:~# LIBGL_DEBUG="verbose" glxinfo
name of display: :0.0                         
libGL: XF86DRIGetClientDriverName: 0.0.10 nouveau (screen 0)
libGL: OpenDriver: trying /usr/local/lib/dri/nouveau_dri.so 
drmOpenDevice: node name is /dev/dri/card0                  
drmOpenDevice: open result is 5, (OK)                       
drmOpenByBusid: Searching for BusID pci:0000:01:00.0        
drmOpenDevice: node name is /dev/dri/card0                  
drmOpenDevice: open result is 5, (OK)                       
drmOpenByBusid: drmOpenMinor returns 5                      
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0        
libGL error:                                                
Can't open configuration file /etc/drirc: No such file or directory.
libGL error:                                                        
Can't open configuration file /root/.drirc: No such file or directory.
display: :0  screen: 0                                                
[COLOR="Red"]direct rendering: Yes[/COLOR]                                                 
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
OpenGL vendor string: Tungsten Graphics, Inc. and nouveau                     
OpenGL renderer string: Gallium 0.2, NV40 on Nouveau/DRI                                                                                                               
OpenGL version string: 1.5 Mesa 7.3-devel                                                                                                                              
OpenGL extensions:                                                                                                                                                     
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program,                                                                                                
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,                                                                                                   
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,                                                                                          
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,                                                                                            
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,                                                                                                                       
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,                                                                                                               
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,                                                                                                                                 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,                                                                                                                               
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,                                                                                                                                    
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,                                                                                                                      
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,                                                                                                                                      
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax,                                                                                                                                             
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,                                                                                                                                           
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_object,                                                                                                                                                              
    GL_EXT_framebuffer_blit, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,                                                                                                                                                
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,                                                                                                                                                                                       
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_separate_stencil, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xfb 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0xfc  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xfd  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xfe  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xff  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x108  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x109  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x10a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x10b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x10c  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x10d  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x10e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x10f  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x118  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x119  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x11a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x11b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

As you can see,I don't seem to have a drirc installed,I've just tried compiling the source code for driconf,but it doesn't seem to work,can you give me any advice on that one?

Also to let you know,I still have AIGLX set to on in my xorg.conf.

Regards,
        STEVE555

---

### Post by RAOF on 2008-12-27
> **STEVE555 said:**
> ...
As you can see,I don't seem to have a drirc installed,I've just tried compiling the source code for driconf,but it doesn't seem to work,can you give me any advice on that one?
...

You don't need a drirc; that's just a configuration file to set various DRI options.

---

### Post by STEVE555 on 2008-12-28
Hi RAOF,
       I've recently had to a re-install because I accidentally messed up my system.

I've been trying to re-install the nouveau driver folllowing the instructions but I'm getting this error when I run startx,(attached with this post).

I've installed your nouveau-kernel-source and my latest kernel is now  2.6.28-4-generic .

I hope you can help me with this one,

Regards,
       STEVE555

---

