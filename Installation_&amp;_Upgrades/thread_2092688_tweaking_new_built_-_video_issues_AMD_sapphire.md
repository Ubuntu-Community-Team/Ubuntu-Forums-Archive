---
title: "tweaking new built - video issues AMD sapphire"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Eklod on 2012-12-08
Hello:

Loaded the latest 64bit Studio distro 12.04 on new hardware: 
Gygabyte mb 970A-D3
AMD FX8 cpu 
sapphire hd7770 
8 gig Kingston hyperX RAM

I experience intemittent display corruption issues- some program windows dont get refreshed.  Only way to clear is to maximize another window or switch desktop.  Happening with all the screen size and resolutions combinations.  I reloaded the AMD Catalyst driver and tried all available versions, settings combinations, no success.  I currently run the latest version:  8.96.7-120312a-135598C-ATI.   Removing all checkmarks under Windows Manager Tweaks/Cycling reduced those occurences and it no longer affects toolbar icons, but it still occurs in Firefox and ZinSynthetizer (the problem was most noticeable under  GoogleEarth, which was unusable.  It is now working flawlessly).   Any suggestions to get rid of this issue entirely?  

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series
OpenGL version string: 4.2.11627 Compatibility Profile Context

lsmod | grep fglrx
fglrx                3206073  188

glxinfo | grep direct
direct rendering: Yes
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_EXT_direct_state_access, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 

Thank you

---

