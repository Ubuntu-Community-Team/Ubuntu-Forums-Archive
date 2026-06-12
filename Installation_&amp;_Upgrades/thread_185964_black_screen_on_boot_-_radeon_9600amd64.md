---
title: "black screen on boot - radeon 9600/amd64"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by bmilner on 2006-06-01
After upgrading to 6.06 from 5.10, I no longer have video after a certain point in the boot process. The last message I see is something about hal deamon starting and then the screen goes black. Alt-F1 etc have no effect. 

The kernel is  2.6.15-23-amd64-generic and I have an ATI Technologies, Inc. Radeon 9600 (R300 AP) that was working properly on the last release. 

Any ideas on how to debug this? I am fairly new to ubuntu linux (old hat to redhat).


I see these messages in syslog and assume they are related,

[   64.049497] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[   64.933205] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   64.933220] agpgart: Badness. Don't know which AGP mode to set. [bridge_agpst
at:1f000a0a vga_agpstat:ff00021b fell back to:- bridge_agpstat:1f000208 vga_agpstat:ff00021b]
[   64.933223] agpgart: Bridge couldn't do AGP x4.
[   64.933229] agpgart: Putting AGP V3 device at 0000:00:00.0 into 0x mode
[   64.933281] agpgart: Putting AGP V3 device at 0000:01:00.0 into 0x mode

[   69.264076] [drm] Setting GART location based on new memory map
[   69.264087] [drm] Loading R300 Microcode
[   69.273656] [drm] writeback test failed

---

### Post by bmilner on 2006-06-02
Ok, some more information about this problem.

I had an unkillable Xorg process that was using all cpu. After searching on the net for this, it seems that AGP speed is detected wrong and is causing this problem. When I change the bios to 4x speed instead of 8x speed, I can then start X. It seems this is a kernel AGP detection problem that is new to my setup.

---

### Post by kurush on 2006-06-03
I have the exact same problem with a radeon 9800, nforce2, and amd k6.  The 4x workaround works, but is there a "real" fix for this?

---

### Post by bmilner on 2006-06-07
I filed a bug report, [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48053](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48053) ,  but still have no clue as to what is causing this.  It is hard to diagnose because both the kernel and xorg have changed with this release. I did manage to get X up with a breezy kernel. I suspect that the kernel is reporting AGP differently to xorg and that xorg is then requesting and invalid AGP mode which then completly hoses the startup of xorg.

---

