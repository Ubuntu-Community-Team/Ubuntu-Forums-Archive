---
title: "Broken 10.4 Lucid install--can't get fglrx"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MattPhillips on 2010-03-30
Hi,

I'm trying to get Ubuntu to run on a Mac but I haven't been able to get anywhere with OpenGL graphics (which I need).  It seems to be a driver issue--I'm using an ATI X1900 XT (now legacy according to ATI's website).  Under 9.10, I got 'assertion-gtk' errors (or something like this) when I tried to run glxgears or even just glxinfo; I downloaded EnvyNG which looked like exactly what I needed, but it didn't work.  I found a thread in which a similar problem was 'resolved' through an upgrade to 10.4, so I tried that.  

Unfortunately, for me the problem seems to persist.  During the install I got an error/warning saying fglrx had not been installed, nor had 3 packages which depend on it.  I even got an 'upgrade aborted' message box, but in fact I am in 10.4 now as I write this (after restarting, getting upgrades) so never mind that, I guess.  EnvyNG now doesn't even launch.  

I have the european-style 'do not enter' icon on my taskbar; when I mouseover, it says that an installation error occurred with error message 'Error: BrokenCount>0'.  When I click the icon, the Update Manager opens, and there is fglrx, 'new install'.  If I try to install it, I first get a warning message box, 'You have 1 broken package on your system!  Use the 'Broken' filter to find it'.  I close this, then I get an error dialog with this error string:

> E: /var/cache/apt/archives/fglrx_2%3a8.721-0ubuntu7_i386.deb: subprocess new pre-installation script returned error exit status 2

And finally after I close this I get a 'update complete but errors occurred' dialog.  I found no way to simply copy the text in the 'details' section, so I've included a screenshot of that dialog as an attachment.

Lastly: Here's my glxinfo output, pretty predictable at this point--

> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Can anybody help me get fglrx on my system?  Thank you--

Matt

---

### Post by ppp0 on 2010-03-31
Same problem!

---

### Post by MattPhillips on 2010-03-31
Okay, 'resolved'--it's bug #546917,

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/546917](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/546917)

A fix is described there, I'm working on that now.  In the meantime it wouldn't be a bad idea for people reading this who have the same problem to go that page and click the 'yes this affects me too'  button, it might get more attention that way (the current fix is a little high-level for me, it would be great to get a more hold-my-hand version).

Matt

---

### Post by descendent87 on 2010-03-31
What version of catalyst are you trying to install? Apparently 9.4 will drop support for your card so you will have to use the open source drivers soon.
Out of interest what was wrong with the open source drivers? They work a lot better for me than fglrx ever did (using a Radeon HD3200)

---

### Post by clhsharky on 2010-03-31
HI MattPhillips

#1 OpenGL graphics is suported in radeon driver in Lucid, here is my glxinfo for Radeon X1650 card.

```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV530 71CD) 20090101  TCL DRI2
OpenGL version string: 1.5 Mesa 7.9-devel
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_provoking_vertex, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_MESAX_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

```

#2> ATI X1900 XT (now legacy according to ATI's website
Is correct, fglrx doesn't support r5xx cards 'your card' since cat 9.3 and Ubuntu 8.10. You can still use Ubuntu 8.04 'still supported' with cat 9.3 if you want to use fglrx.

#3 Bug 
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/546917](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/546917)

is for a supported card 'ATI Technologies Inc R700 [Radeon HD 4850]'and not your R500 card. So I do not see how it will resolve your problem.

#4 Clean out all fglrx install attempts and reinstall radeon driver. Making sure

xserver-xorg 1:7.5+3ubuntu1
libgl1-mesa-glx 7.7-4ubuntu1
libdrm2 2.4.18-1ubuntu2
xserver-xorg-video-ati 1:6.12.191-1ubuntu2

or higher is installed.

Sharky

---

### Post by MattPhillips on 2010-03-31
Hi,

When I posted originally I didn't realize/remember that fglrx is proprietary and there is an open-source option.  Unfortunately, I didn't get very far trying to follow the setup options here:

[URL="https://help.ubuntu.com/community/RadeonDriver"]

As mentioned earlier, glxinfo just gave me error strings and trying to install mesa failed:

> matt@matt-desktop:/etc/modprobe.d$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fglrx-amdcccle: Depends: fglrx but it is not going to be installed
  fglrx-kernel-source: Depends: fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

After apt-get install -f I got the same/similar error as before:

> matt@matt-desktop:/etc/modprobe.d$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 kdebase-runtime-data-common fglrx
  libboost-program-options1.38.0 libknotificationitem1 libexiv2-5 liblzma0
  sdparm kdebase-runtime-bin-kde4 python-sip4 dkms fglrx-amdcccle
  libpolkit-dbus2 fglrx-kernel-source libqt4-phonon khelpcenter4 libpolkit-qt0
  linux-headers-2.6.31-14-generic libpolkit-grant2 libpolkit2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 97 not upgraded.
2 not fully installed or removed.
Need to get 0B/18.2MB of archives.
After this operation, 59.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 184044 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.721-0ubuntu7_i386.deb) ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/xorg/modules/extensions/libdri.so to /usr/lib/fglrx/libdri.so.xlibmesa by fglrx'
  found `diversion of /usr/lib/xorg/modules/extensions/libdri.so to /usr/lib/fglrx/libdri.so.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.721-0ubuntu7_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.721-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I gave up with open source drivers at this point.  As for which version of Catalyst, I don't know--where would I find that out?  Thanks--

Matt

---

### Post by clhsharky on 2010-03-31
HI MattPhillips

Here I believe
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)

Sharky

---

### Post by ppp0 on 2010-03-31
> **MattPhillips said:**
> Okay, 'resolved'--it's bug #546917,

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/546917](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/546917)

A fix is described there, I'm working on that now.  In the meantime it wouldn't be a bad idea for people reading this who have the same problem to go that page and click the 'yes this affects me too'  button, it might get more attention that way (the current fix is a little high-level for me, it would be great to get a more hold-my-hand version).

Matt

Sorry but i didn't find there steps to resolve this bug :-/

---

### Post by MattPhillips on 2010-03-31
Thanks much Sharky, I ran the installer and here's what happened:

> matt@matt-desktop:~/Desktop$ sh ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.DTHIa7
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-18-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.DTHIa7

I guess I'm going to try to get the open source drivers to work, but things haven't gotten off to a great start there either (see prev. post).

ppp0, see Sharky's first post--that bug report/fix may not help you.  But the post by David Mack seemed to provide a solution for someone with the right card, who knows what they're doing.

Matt

---

### Post by clhsharky on 2010-03-31
HI 

Cat 9.3 is for Ubuntu 8.04 or 8.10.

If you want Lucid you need radeon.

Sharky

---

### Post by descendent87 on 2010-03-31
The open source drivers are included in lucid, no need to do anything from a clean install. if you've messed up and cant boot to gui you could just grab the daily image and reinstall using that

---

### Post by clhsharky on 2010-03-31
HI Matt

The best part of running the radeon driver is you can run the latest drivers and kernel. This is what Im running on my radeon X1650 box.

distro: Ubuntu
 codename: lucid
 architecture: x86_64
Kernel2.6.34-999 daily
xserver-xorg 1:7.5+3ubuntu1
libgl1-mesa-glx 7.9.0~git20100330
libdrm2 2.4.19+git2010031
xserver-xorg-video-ati 1:6.12.192+git20100324.53ac0616-OubuntuOsarvatt

And has been stable


Sharky

---

