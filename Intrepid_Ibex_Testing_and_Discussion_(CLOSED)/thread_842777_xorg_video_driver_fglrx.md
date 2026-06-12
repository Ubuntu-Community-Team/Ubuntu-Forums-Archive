---
title: "xorg video driver fglrx"
date: 2008-06-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eeclark on 2008-06-27
I am jealous.  I keep seeing these updates in the repos for xorg video drivers but none of them are fglrx.

Anyone know when to expect it?

Thanks

---

### Post by soccerboy on 2008-06-27
probably in a few weeks when the development branch stabilizes.

---

### Post by eeclark on 2008-06-28
With Alpha 1 now out I see ATI and Radeon drivers got updated.
Where's the fglrx love?

---

### Post by soccerboy on 2008-06-28
> **eeclark said:**
> With Alpha 1 now out I see ATI and Radeon drivers got updated.
Where's the fglrx love?

Again, ati and radeon drivers are now open source so they can be built into the kernel.  fglrx are patched in after the kernel is stable.

---

### Post by eeclark on 2008-06-28
Trying to get compiz effects (Desktop Effects) working with the ATI or Radeon drivers...no luck.
I thought that it worked with the ATI driver in the past.
I know it has worked with fglrx, but since I do not have the fglrx driver I cannot get compiz effects to work.

---

### Post by soccerboy on 2008-06-28
> **eeclark said:**
> Trying to get compiz effects (Desktop Effects) working with the ATI or Radeon drivers...no luck.
I thought that it worked with the ATI driver in the past.
I know it has worked with fglrx, but since I do not have the fglrx driver I cannot get compiz effects to work.

You could always patch it in yourself.  Or have you tried the open source drivers for your card, maybe they work now.

---

### Post by eeclark on 2008-06-28
Tried to open source drivers.
They work but no compiz.

```

edward@smallville:~$ lsmod | grep radeon
radeon                136352  2 
drm                    84264  3 radeon
edward@smallville:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.4

Segmentation fault
edward@smallville:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.4

```

---

### Post by eeclark on 2008-06-28
Maybe the ATI driver isn't loading...
I get the same results in lsmod and glxinfo whether I use 'ati' or 'radeon' in my xorg.conf
My card is a 9600 Pro Turbo.

This is using the 'ati' driver. (previous post was with radeon driver)
```

edward@smallville:~$ lsmod | grep ati
cpufreq_conservative    14472  0 
rsrc_nonstatic         19200  1 yenta_socket
pcmcia_core            44180  3 pcmcia,yenta_socket,rsrc_nonstatic
edward@smallville:~$ lsmod | grep radeon
radeon                136352  2 
drm                    84264  3 radeon
edward@smallville:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.4

```

---

### Post by soccerboy on 2008-06-28
sorry I don't have much experience with radeon or radeonhd (opensource ati) drivers.  if you want help with that, you could post in one of those threads.  I am not positive, but I am pretty sure that fglrx won't be patched until kernel is stable.  You could build your own copy of the kernel if you have experience with that or would like to give it a try.

---

### Post by RAOF on 2008-06-28
> **eeclark said:**
> Tried to open source drivers.
They work but no compiz.
...

Do you still have the fglrx drivers installed (your use of fglrxinfo suggests so).  If so, remove them.  Like the nvidia drivers, having them installed breaks all other 3d drivers.

---

### Post by eeclark on 2008-06-29
I removed it, but got the error message that it failed to remove the /usr/lib/fglrx folder.

```

edward@smallville:~$ sudo apt-get remove xorg-driver-fglrx 
[sudo] password for edward: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpostproc1d discover-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 34.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127617 files and directories currently installed.)
Removing xorg-driver-fglrx ...
 * Stopping atieventsd                                                   [ OK ] 
rmdir: failed to remove `/usr/lib/fglrx': Directory not empty
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
edward@smallville:~$ 

```

The radeon and ati drivers work now.
THanks

---

