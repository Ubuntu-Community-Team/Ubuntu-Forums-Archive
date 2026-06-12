---
title: "Radeon xorg crack for R6XX-R7XX fails with: RADEONDRIGetVersion failed to open the DR"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ExtenzJunkie on 2009-09-24
I'm a relative noob to linux so forgive me if I don't document this right.

I can run on both monitors with no problems using xrandr. This is Karmic Alpha 6 with most recent updates and addition of edgers crack.

Now, I've been trying to get compiz to run on my dual-head set up, and I'm getting the following error in my Xorg log:

drmOpenDevice: node name is /dev/dri/card0
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): using shadow framebuffer

Compiz then complains:
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA:     Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2960x1050) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

This is using the PPA drm modules for 6xx-7xx 3d support (2.4.3+git20090831+r6xx-r7xx-3d.8e297c0a-0ubuntu0tormod4).
Loaded the source and installed with module-assitant.

My mobo is is a Gigabyte MA790GPT with a built in HD3300 graphics card (R780?). Phenom X2s, 4GB RAM, uh... HannsG 22" widescreen LCD on DVI and 19" Samsung LCD on VGA.

Relevant sections from xorg.conf:
Section "Device"
        Identifier "HD3300 Onboard"
        BusID   "PCI:1:5:0"
        Driver "ati"
        Option "DRI"    "true"
EndSection

Section "Screen"
        Identifier "Main Screen"
        Device "HD3300 Onboard"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1680x1050_60"
                Virtual 2960 1050
        EndSubSection
EndSection

Section "Extensions"
        Option "RENDER" "True"
        Option "DAMAGE" "True"
        Option "Composite" "True"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "ServerFlags"
        Option "AIGLX" "True"
        Option "DontZap"  "False"
EndSection

lspci:
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics

dmsg| grep drm:
[   41.750258] [drm] Initialized drm 1.1.0 20090831agd5f
[   41.794793] [drm] Initialized radeon 1.29.0 20080613 on minor 0

Installed (only the relevant stuff):

ii xorg 1:7.4+3ubuntu5 X.Org X Window System
ii xorg-docs-core 1:1.4-5 Core documentation for the X.org X Window System
ii xserver-xorg 1:7.4+3ubuntu5 the X.Org X server
ii xserver-xorg-core 2:1.6.3+git20090805+server-1.6-branch.f274e595-0ubuntu0sarvatt Xorg X server - core server
ii xserver-xorg-dev 2:1.6.3+git20090805+server-1.6-branch.f274e595-0ubuntu0sarvatt Xorg X server - development files
ii xserver-xorg-video-radeon 1:6.12.99+git20090920.97a4e747-0ubuntu0tormod X.Org X server -- ATI Radeon display driver
ii xserver-xorg-video-radeonhd 1.2.5+git20090921.ee508b37-0ubuntu0tormod X.Org X server -- AMD/ATI r5xx, r6xx display driver
ii drm-modules-2.6.31-10-generic 2.4.3+git20090831+r6xx-r7xx-3d.8e297c0a-0ubuntu0tormod4+2.6.31-10.35 DRM rendering modules for Linux (kernel 2.6.31-10-generic
ii drm-modules-source 2.4.3+git20090831+r6xx-r7xx-3d.8e297c0a-0ubuntu0tormod4 Source for the DRM kernel rendering modules
ii libdrm-intel1 2.4.14-0ubuntu0tormod Userspace interface to intel-specific kernel DRM services
ii libdrm-radeon1 2.4.14-0ubuntu0tormod Userspace interface to radeon-specific kernel rendering s
ii libdrm2 2.4.14-0ubuntu0tormod Userspace interface to kernel DRM services -- runtime

Kernel is: 2.6.31-10-generic (x86_64)

Out of kern.log (after running compiz):
Sep 24 12:45:17 hallix64 kernel: [  747.852058] mtrr: no MTRR for c0000000,10000000 found
Sep 24 12:45:17 hallix64 kernel: [  983.862599] mtrr: no MTRR for c0000000,10000000 found
Sep 24 12:45:17 hallix64 kernel: [ 1042.333634] mtrr: no MTRR for c0000000,10000000 found
Sep 24 12:45:17 hallix64 kernel: [ 1354.052149] mtrr: no MTRR for c0000000,10000000 found
Sep 24 12:45:17 hallix64 kernel: [ 1444.373119] compiz.real[6510]: segfault at 97aa ip 000000000041036e sp 00007fff495d1320 error 4 in compiz.real[400000+3c000]
Sep 24 12:45:17 hallix64 kernel: [ 1444.389920] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:29:05 hallix64 kernel: [ 1768.989319] npviewer.bin[7077]: segfault at f5309044 ip 00000000f7740ded sp 00000000ffa57684 error 4 in libpthread-2.10.1.so[f7739000+16000]
Sep 24 13:29:05 hallix64 kernel: [ 1769.215906] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:29:05 hallix64 kernel: [ 1880.860928] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:29:05 hallix64 kernel: [ 1948.398635] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:29:05 hallix64 kernel: [ 2075.273620] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:29:05 hallix64 kernel: [ 4377.423263] radeon 0000:02:00.0: PCI INT A disabled
Sep 24 13:29:05 hallix64 kernel: [ 4377.437465] [drm] Module unloaded
Sep 24 13:29:05 hallix64 kernel: [ 4396.296613] [drm] Initialized drm 1.1.0 20090831agd5f
Sep 24 13:29:05 hallix64 kernel: [ 4396.374266] radeon 0000:01:05.0: setting latency timer to 64
Sep 24 13:45:36 hallix64 kernel: [ 4396.374580] [drm] Initialized radeon 1.29.0 20080613 on minor 0
Sep 24 13:45:36 hallix64 kernel: [ 4396.375521] radeon 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 24 13:45:36 hallix64 kernel: [ 4396.375533] radeon 0000:02:00.0: setting latency timer to 64
Sep 24 13:45:36 hallix64 kernel: [ 4396.375911] [drm] Initialized radeon 1.29.0 20080613 on minor 1
Sep 24 13:45:36 hallix64 kernel: [ 4417.656939] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:45:36 hallix64 kernel: [ 4750.732519] mtrr: no MTRR for c0000000,10000000 found
Sep 24 13:45:36 hallix64 kernel: [ 5387.773901] ttm: Unknown symbol drm_mm_get_block_generic
Sep 24 13:45:36 hallix64 kernel: [ 5387.774201] ttm: disagrees about version of symbol drm_mm_takedown
Sep 24 13:45:36 hallix64 kernel: [ 5387.774206] ttm: Unknown symbol drm_mm_takedown
Sep 24 13:45:36 hallix64 kernel: [ 5387.774391] ttm: disagrees about version of symbol drm_mm_put_block
Sep 24 13:45:36 hallix64 kernel: [ 5387.774396] ttm: Unknown symbol drm_mm_put_block
Sep 24 13:45:36 hallix64 kernel: [ 5387.774842] ttm: disagrees about version of symbol drm_mm_search_free
Sep 24 13:45:36 hallix64 kernel: [ 5387.774847] ttm: Unknown symbol drm_mm_search_free
Sep 24 13:45:36 hallix64 kernel: [ 5387.775816] ttm: Unknown symbol drm_mm_pre_get
Sep 24 13:45:36 hallix64 kernel: [ 5387.776246] ttm: Unknown symbol drm_mm_clean
Sep 24 13:45:36 hallix64 kernel: [ 5387.776548] ttm: disagrees about version of symbol drm_mm_init

glxinfo says:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

Right after I leave grub at boot, I get this error (though, I have no idea if it's related):
[    0.176553] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.176553] pci 0000:00:00.0: BAR 3: can't allocate resource

I have no idea what that means, but it doesn't sound good.

Seems like I should have a /dev/dri, and I don't.  Not even the directory.

Happy to provide more info if it helps, but hopefully that gives you an idea of what's going on.  

Thanks for any clues.

---

### Post by overdrank on 2009-09-24
Moved to Karmic Koala Testing and Discussion

---

