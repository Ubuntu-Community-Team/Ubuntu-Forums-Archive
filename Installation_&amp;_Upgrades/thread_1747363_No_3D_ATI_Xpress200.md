---
title: "No 3D ATI Xpress200"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by keithclark on 2011-05-02
I just upgraded to 11.04 and now I cannot get 3D working again for my ATI Xpress200 video card.  This card worked very well in past releases.

I have fglrx installed but I cannot seem to figure out what is going wrong.  I have the same card on another computer and it works fine!

I am trying to use the open source drivers and here is the output of dmesg | grep drm

keithclark@HP1211N:~$ dmesg | grep drm
[   12.585933] [drm] Initialized drm 1.1.0 20060810
[   14.049018] [drm] radeon defaulting to kernel modesetting.
[   14.049023] [drm] radeon kernel modesetting enabled.
[   14.056125] [drm] initializing kernel modesetting (RS480 0x1002:0x5954).
[   14.056163] [drm] register mmio base: 0xFDDF0000
[   14.056165] [drm] register mmio size: 65536
[   14.056423] [drm] Generation 2 PCI interface, using max accessible memory
[   14.056445] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.056447] [drm] Driver supports precise vblank timestamp query.
[   14.056457] [drm] radeon: irq initialized.
[   14.056554] [drm] Detected VRAM RAM=64M, BAR=128M
[   14.056558] [drm] RAM width 128bits DDR
[   14.056658] [drm] radeon: 64M of VRAM memory ready
[   14.056660] [drm] radeon: 512M of GTT memory ready.
[   14.056687] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.059681] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   14.067797] [drm] Loading R300 Microcode
[   14.305729] [drm] radeon: ring at 0x00000000A0001000
[   14.305751] [drm] ring test succeeded in 3 usecs
[   14.305879] [drm] radeon: ib pool ready.
[   14.306034] [drm] ib test succeeded in 0 usecs
[   14.306398] [drm] Radeon Display Connectors
[   14.306400] [drm] Connector 0:
[   14.306402] [drm]   VGA
[   14.306404] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   14.306406] [drm]   Encoders:
[   14.306407] [drm]     CRT1: INTERNAL_DAC2
[   14.459634] [drm] fb mappable at 0xD8040000
[   14.459638] [drm] vram apper at 0xD8000000
[   14.459639] [drm] size 4177920
[   14.459641] [drm] fb depth is 24
[   14.459642] [drm]    pitch is 5440
[   14.527539] fb0: radeondrmfb frame buffer device
[   14.527541] drm: registered panic notifier
[   14.527553] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0

So I think that the open source driver is installed correctly, but I think the problem with the the opengl driver:

keithclark@HP1211N:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

---

### Post by Mark Phelps on 2011-05-03
There are no fglrx drivers that work with your card and Ubuntu 11.04; in fact, there have been no such drivers since Ubuntu 9.04. 

Unless, you found and loaded drivers from a ppa for your previous Ubuntu version.

The only drivers available now are the open-source drivers and they are installed by default.

---

### Post by keithclark on 2011-05-03
> **Mark Phelps said:**
> There are no fglrx drivers that work with your card and Ubuntu 11.04; in fact, there have been no such drivers since Ubuntu 9.04. 

Unless, you found and loaded drivers from a ppa for your previous Ubuntu version.

The only drivers available now are the open-source drivers and they are installed by default.

Well, I've uninstalled all video drivers and re-installed the open source ones.  Still not working though.

Keith

---

### Post by keithclark on 2011-05-03
Bug report filed:  Bug #776737

Keith

---

