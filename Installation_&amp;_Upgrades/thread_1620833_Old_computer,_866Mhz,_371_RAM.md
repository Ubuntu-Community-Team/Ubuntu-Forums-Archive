---
title: "Old computer, 866Mhz, 371 RAM"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by SpinningAround on 2010-11-13
I have an old computer that is currently running Ubuntu 9.04, problem is that the support for this version have ceased. The computer is working quite fine atm but lacks updates, watching flash isn't possible but guess it's caused by the hardware. I'm thinking on a fresh install with some version of ubuntu 10.04 since it's LTS. One think that make me hesitate is that the graphic card is from ATI (Rage 128 PF/PRO).

Question what version to use, lubuntu, xubuntu? If ATI Rage 128 is supported, basic support since it will only be used for writing, email and surfing.

Below:
lspci -v | grep VGA
free -m
cat /proc/cpuinfo
lspci
glxinfo -v

**Card info.**
```

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
	Subsystem: ATI Technologies Inc Device 0018
	Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 10
	Memory at d4000000 (32-bit, prefetchable) [size=64M]
	I/O ports at a000 [size=256]
	Memory at d9000000 (32-bit, non-prefetchable) [size=16K]
	[virtual] Expansion ROM at d8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: aty128fb


```

**free -m**
```
             total       used       free     shared    buffers     cached
Mem:           371        337         33          0          6         90
-/+ buffers/cache:        240        131
Swap:          705         24        681

```

**cat /proc/cpuinfo**
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 8
model name	: Pentium III (Coppermine)
stepping	: 6
cpu MHz		: 866.615
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips	: 1733.23
clflush size	: 32
power management:

```

**lspci**
```

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:08.3 FireWire (IEEE 1394): NEC Corporation uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller (rev 01)
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0c.0 Communication controller: Rockwell International HSF 56k Data/Fax/Voice Modem (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

```

Current **glxinfo**
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Rage 128 Pro 20051027 AGP 1x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 7.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

16 GLX Visuals
Visual ID: 21  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 22  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 4e  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 4f  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 50  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 51  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 52  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 53  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 54  depth=24  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 55  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 56  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 57  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 58  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 59  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 5a  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 5b  depth=24  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.

16 GLXFBConfigs:
Visual ID: 3e  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 3f  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 40  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 41  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 42  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 43  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 44  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 45  depth=0  class=TrueColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 46  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 47  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 48  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 49  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 4a  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 4b  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.
Visual ID: 4c  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=None
    Opaque.
Visual ID: 4d  depth=0  class=DirectColor
    bufferSize=24 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=0
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    visualCaveat=Slow
    Opaque.

```

---

### Post by searchfgold6789 on 2010-11-13
Xubuntu will enable you to compute at an advanced, very Ubuntu-like level while managing your resources (RAM, HD space) wisely. I have used it for about a year and it has served me very well on a computer with 750 MhZ CPU, and 512 RAM with cruddy graphics.

Lubuntu is somewhat minimalist and is focused on simply not using as many resources, as opposed to managing them cleverly. I have tried both and either will suit your needs (not many) very well.

---

