---
title: "fglrx working, xorg.conf ok, but no direct rendering"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by gelse on 2005-09-15
the problem is - again - direct rendering with ati.
first some infos:

modinfo fglrx:
```

filename:       /lib/modules/2.6.12custom/kernel/drivers/char/drm/fglrx.ko
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
vermagic:       2.6.12custom preempt PENTIUM4 gcc-3.4
depends:        agpgart
parm:           firegl:s

```

some lines from /var/log/Xorg.0.log
```

(II) fglrx(0): pEnt->device->identifier=0x82136a0
...
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"
..
(**) fglrx(0): Option "MonitorLayout" "AUTO, NONE"
..
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
..
(**) fglrx(0): Option "UseFastTLS" "2"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "on"
..
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(**) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "MOBILITY RADEON 9000 (M9 4C66)" (Chipset = 0x4c66)
(--) fglrx(0): (PciSubVendor = 0x1019, PciSubDevice = 0xb732)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original AT I
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xe8100000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9000
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: M9
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): No EDID information available.
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is enabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 14 modes found for primary display.
.. Liste der modes - ist mir mal egal, 1280x1024 ist auch ok, wenn DR laufen würde...
(==) fglrx(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 6.8.0, module version = 8.16.20
        ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x000009db
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(**) fglrx(0): using built in AGPGART module: yes
(**) fglrx(0): UseFastTLS=2
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
.. die liste erspar ich euch auch mal...
(II) fglrx(0): UMM Bus area:     0xf0701000 (size=0x038ff000)
(II) fglrx(0): UMM area:     0xf0701000 (size=0x038ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports
.. die failures bei den probes ausgeschnitten
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xe0b91000
(II) fglrx(0): [drm] mapped SAREA 0xe0b91000 to 0xb7ae1000
(II) fglrx(0): [drm] framebuffer handle = 0xf0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12custom
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe8100000
(II) fglrx(0): [agp] Mode=0x1f000207 bridge: 0x1039/0x0646
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000304
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000304 )
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xe0d01000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "IgnoreEDID" is not used
(WW) fglrx(0): Option "NoTV" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
..

```

should work, fglrx is loaded and says that direct rendering is enabled.
but, sadly:
```

gelse@w220-3:~$ /usr/X11R6/bin/fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

of course i checked the xorg.conf, everything should be fine there (changed and tested some settings (UseInterntalAGPGART for example), of course, but nothing helped - it stayed EXACTLY the same.)
```

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

    Driver      "vga"
EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
    #Option                              "NoDDC"
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
    Option "DesktopSetup"               "0x00000100"
    Option "MonitorLayout"              "AUTO, NONE"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified"
    Option "VRefresh2"                  "unspecified"
    Option "ScreenOverlap"              "0"
...
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "on"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
...
# === Misc Options ===
    Option "UseFastTLS"                 "2"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4c66
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1400x1050" "1280x1024" "1024x768" "800x600"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"

    Identifier  "Server Layout"
    Screen "Screen0"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Touchpad" "CorePointer"

EndSection

```

glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

what i did:
i followed this guide exactly:
[http://www.ubuntuforums.org/showthread.php?p=348911](http://www.ubuntuforums.org/showthread.php?p=348911)
searched in the web, tried some of the solutions there (they all are basically the same, if you follow this guide [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html) and the one above, you covered them all).
kernel configuration should be perfect, (following stanchina)
xorg should be perfect (following stanchina, and trying myself - no effect)
packages should be perfect (following the post in the forum above)
still dont works...

so summary:
fglrx installed correctly, compiled und loaded
xorg works with its config and the driver (fglrx used @ lsmod, and i see the screen at 1280x1024 and centered)
in the logfile, xorg says, fglrx has direct rendering enabled.
but STILL when i use glxinfo or fglrxinfo it says MESA ...

i already uninstalled xorg and everything related to graphics (mesa and fglrx) and deleted everything with the string fglrx in it from the system (as mentioned in some posts), reinstalled everything - no result.

finally something from /usr/src/linux/.config
```

CONFIG_AGP=m
CONFIG_AGP_ATI=m
CONFIG_DRM=m
CONFIG_DRM_RADEON=m
# CONFIG_FB is not set                 (but xorg is still working with FB? strange.)
CONFIG_BLK_DEV_SIS5513=y

```

that should be everything important - if i missed anything, let me know.

i have absolutely NO clue why direct rendering isnt working. it should, but it doesnt. oh, yes - and some say i should use the older ati-driver - but as far as i read that only affects the resolution thingy (which isnt that important).

and i know that direct rendering COULD work, because i had debian/unstable with xfree a few days ago, and it worked fine there.

in spite of the fact that i fear that several of my other hardware (external USB-soundcard, very handy for using TeamSpeak without losing sound on the entire rest of the system) wont work any more,perhaps i should change to gentoo, i dont like it - but if it works....

can anyone PLEASE help me with some ideas?


(and please put this thread to the right forum - i cant do it myself and made a mistake first. thanks.)

---

### Post by gelse on 2005-09-15
just stumbled across [http://ubuntuforums.org/showpost.php?p=347871](http://ubuntuforums.org/showpost.php?p=347871). forgot to mention that i had the DRI version mismatch problem too, and solved it like described in that thread.
about  libstdc++5 - i got libstdc++6, the 5 is not available in breezy ...

oh, and sorry - this should be in the breezy forum, any moderator please put it there.

---

### Post by mlomker on 2005-09-15
Bottom line is probably that the /usr/X11R6/lib/libGL.so.1.2 file didn't get overwritten...or it was overwritten when you did a package upgrade subsequent to install.  That file is the key to MESA vs. ATI in fglrxinfo.

```

root@mlomkernote:/ # ls -l /usr/X11R6/lib/libGL.so.1.2
-rwxr-xr-x  1 root root 1009781 2005-06-08 14:07 /usr/X11R6/lib/libGL.so.1.2

```

Not sure when you did my how-to but I've been improving it a little each day.  Try running it again using the **dpkg -i --force-overwrite packagename.deb** command this time. 

I take it you compiled your own kernel?  If you remove the internal AGP Gart then you should get even better performance than the rest of us.

---

### Post by gelse on 2005-09-15
i already thought that the libGL is the part - but to avoid exactly that i did the --force-all when i installed it - and didnt get any errors.

here a short ls -l list of all the libGL.so.1.2 on my system (right at the moment, after updatedb and locate)
```

-rw-r--r--   1 root root 403432 Aug 30 07:45 /usr/lib/i686/mmx/cmov/libGL.so.1.2
-rw-r--r--   1 root root 407720 Aug 30 07:45 /usr/lib/libGL.so.1.2
-rwxr-xr-x   1 root root 773505 Aug 16 18:13 /usr/X11R6/lib/libGL.so.1.2

```

found too:
/usr/lib/dri/libGL.so which is a pointer to a nonexiistant file (to libGL.so.1 in the same directory)
and some libGL.so.1 which are pointer to the existant libGL.so.1.2 files in the same directories.

i will try now have a look into the package and check which are the correct libGL.so.1.2 and manually replace the wrong ones. 
(i did that before - but perhaps there were something wrong then instead, because it were even SLOWER then...)

oh, yes - and i did build my own kernel ;) - have to tweak it again, because i still have problems with some hardware (my WLAN-PCMCIA-card, for example)

---

### Post by mlomker on 2005-09-15
Your code box came up empty.  The file is from the xlibmesa-gl package, which you can't remove without removing your entire desktop...hence the requirement to force overwrite on the file and then mess with it whenever they push out an Xorg update.  You'll see the addendum at the bottom of my how-to regarding that.

---

### Post by gelse on 2005-09-15
resultbox should be filled now.

ok, been there, did that - exchanged the /usr/lib/libGL.so.1.2 with the /usr/X11R6/lib/libGL.so.1.2 (which is the right one, comes up with dpkg --contents fglrx-package.deb | grep libGL.so.1.2 and has the exact size, too), restarted X.

result is somehow strange - now i get at glxinfo:
direct rendering: no
...
server glx vendor string: SGI
...
client glx vendor string: ATI
...
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
...


doh!
still no DR ... but at least ATI shows somewhere at glxinfo - :)
checked the /var/log/Xorg.0.log, too - same as quoted above.

tried install the fglrx.deb with --force-overwrite too, no effect.

---

### Post by mlomker on 2005-09-15
Wish I had all the answers, but I don't.  I can only guess that one of the files is not getting replaced.

What are you getting for **dmesg | grep fglrx**?

I'll warn you that I'm grasping at straws now.  Do you have /usr/X11R6/lib in your /etc/ld.so.conf.  Try running ldconfig.

---

### Post by gelse on 2005-09-15
dmesg | grep fglrx gives no output.
i re-checked all libGL.so.1.2 files, all of them are replaced.

anyway, what  making me headaches is /usr/lib/dri/libGL.so which is a pointer to nowhere....

i let it point to the libGL mentioned above, did nothing.

*sigh*

---

### Post by mlomker on 2005-09-15
[QUOTE=gelse]dmesg | grep fglrx gives no output.
[/quote]

Bingo.  Driver isn't even loading.  Make sure you added it to /etc/modules.

I have a similar broken link for that file, except mine is in /usr/lib.

---

### Post by gelse on 2005-09-15
oh, sorry, my fault.
didnt recompile fglrx.ko after the force-overwrite, so the .ko wasnt there.
did that now:

```
root@w220-3:~# dmesg | grep fglrx
[4298056.382000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4298056.385000] [fglrx] Maximum main memory to use for locked dma buffers: 429 MBytes.
[4298056.385000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4298056.386000] [fglrx] module unloaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4298082.010000] [fglrx] Maximum main memory to use for locked dma buffers: 429 MBytes.
[4298082.010000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4298082.012000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4298082.012000] [fglrx] AGP detected, AgpState   = 0x1f000207 (hardware caps of chipset)
[4298082.013000] [fglrx] AGP enabled,  AgpCommand = 0x1f000304 (selected caps)
[4298082.026000] [fglrx] free  AGP = 121909248
[4298082.026000] [fglrx] max   AGP = 121909248
[4298082.026000] [fglrx] free  LFB = 49278976
[4298082.026000] [fglrx] max   LFB = 49278976
[4298082.026000] [fglrx] free  Inv = 0
[4298082.027000] [fglrx] max   Inv = 0
[4298082.027000] [fglrx] total Inv = 0
[4298082.027000] [fglrx] total TIM = 0
[4298082.027000] [fglrx] total FB  = 0
[4298082.027000] [fglrx] total AGP = 32768

```

if i dont get it to work until tomorrow i will change back to hoary 5.04 - and hope it works there. thanks alot for your help. :)

---

### Post by gelse on 2005-09-16
from [http://www.ubuntuforums.org/showthread.php?t=64234](http://www.ubuntuforums.org/showthread.php?t=64234)
> Way to go developers! After all, 8.16 is now being used in linux-restricted-modules as you guys can see on this page: [http://lists.ubuntu.com/archives/breezy-changes/2005-September/011393.html](http://lists.ubuntu.com/archives/breezy-changes/2005-September/011393.html)

So, for every of you that are having problems, update now from the repository, and uninstall any custom attempts  It should work like a breezy

will try that later, i tell you if it works.

if not, i will delete 5.10 and try 5.04 instead - and modify my post if it works.

---

### Post by mlomker on 2005-09-16
[QUOTE=gelse]if i dont get it to work until tomorrow i will change back to hoary 5.04 - and hope it works there. thanks alot for your help. :)[/QUOTE]

That output looks good.  What is fglrxinfo telling you?

Of course you should have tried the Breezy package first!  

My instructions were intended for people that've already tried the **xorg-driver-fglrx** package and had it not work (Hoary includes the 8.8.25 driver that is relatively old).  The Hoary driver did not work for me--just ended up with a black screen.

---

### Post by gelse on 2005-09-16
tried the package today - no effect - same output as usual (logfile says everything is ok, but OpenGL still mesa).
of course after cleaning my system of every fglrx first.

now i switched to hoary - i am at the "DRI doesnt work" step right now, after i made the rpm -> deb -> force-overwrite steps (and building own kernel, of course).
(but now i know where it comes from - at least i hope)

anyway - hoary comes with direct rendering enabled, but glxgears only gives 1600fps - and i know (from my old  system) that with the new driver from ATI i can do 2700fps.

i keep this posting updated - and write something again if i dont get it to work (will switch back to the original drivers then).

thanks :)


update:
```
gelse@w220-3:~$ glxgears
10291 frames in 5.0 seconds = 2058.200 FPS
10747 frames in 5.0 seconds = 2149.400 FPS
10754 frames in 5.0 seconds = 2150.800 FPS
```
... not the 2700 i think i had, but at least more than 1600 ...

what i did:
compile kernel with DRI modular, AND FRAMEBUFFER DISABLED (i bet my right hand that exactly that was the problem when i were at breezy - cant check it, filesystem formatted)!
followed your guide.
exchanged the libdri.a (not sure if that is necessary - exchanged it before i disabled FB in the kernel)
voilá!

perhaps you can update your guide with the information about the framebuffer. on certain laptops that seems to be the problem. and ubuntu comes with framebuffer enabled for default (am i right there?  at least it was enabled after make oldconfig...)

one problem still left, but as far as i know thats a bug with the drivers from ATI:
cant set the resolution to 1400x1050 which would be the native resolution on my laptop.
so - for everyone out there who has the same problem - no workaround at the moment.
but there is an Option which fglrxconfig doesnt ask for :
change
Option "CenterMode"                 "off"
to
Option "CenterMode"                 "on"
in the Device section in your xorg.conf.
that makes your 1280x1024 screen _not_ stretched (and ugly).

---

### Post by gelse on 2005-09-16
*sigh*
all for nothing,
now i have exactly the problem described there:
[http://transgaming.org/forum/viewtopic.php?t=3691](http://transgaming.org/forum/viewtopic.php?t=3691)


just for everyone's information:
the "inside" problem at World of Warcraft is ONLY with the 8.16.20 drivers from ATI - i changed back to the 8.14.13 drivers, and everything is smooth.

---

### Post by mlomker on 2005-09-16
> 
that makes your 1280x1024 screen _not_ stretched (and ugly).

They revamped how the driver autodetects the resolution of the display device.  The problem is that some display devices aren't compliant with the way that they decided to do the check.  On my laptop that means that it defaults to 1024x768 instead of 1280x800.

Downgrading to the 8.14.13 problem solved my issue.  I have a mention of that at the top of the how-to.  Not sure if it's the identical issue to what you're seeing.

I actually don't play games, myself.  I installed the driver simply because I paid for the laptop and I want to use all of what I paid for.  Crazy, eh?

---

### Post by gelse on 2005-09-16
> Not sure if it's the identical issue to what you're seeing.

it is.
but the resolution wouldnt be that much problem - i dont know what they did wrong with the driver, but the resolution-problem AND the problem freezing at certain OpenGL-commands (cant imagine any other reason - it is just that "indoors" doesnt work. i dont know enough about OpenGL that i know what that could be, sadly.) makes me say "that's no good work". ;)

took a look at the framerates, too - they are equal at 8.14.13 and 8.16.20 - what is the benefit, then, practically?

by the way:

CASE SOLVED!

---

### Post by mlomker on 2005-09-16
[QUOTE=gelse]took a look at the framerates, too - they are equal at 8.14.13 and 8.16.20 - what is the benefit, then, practically?[/QUOTE]

They're probably tweaking the code to support their newest cards.  The performance for older cards only goes up by accident while they are working on supporting the new ones.  :-P

---

### Post by digiplaya on 2006-06-17
Well, my install is doing the same thing you had, gelse. Same on pretty much every part of it.

My direct rendering = no, even though everything else seems to check out right. I don't want to downgrade to older drivers either.

I'm running latest MEPIS (sorry to post on ubuntu thread, though mepis is now based on it)

Oh, and here's the relevant section of my Xorg.0.log:
> (II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)

Is there a way to get this module to load properly?

Tom

---

