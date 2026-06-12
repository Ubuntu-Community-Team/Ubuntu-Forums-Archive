---
title: "Kernel 2.6.34 Shutdown and radeon-kms.conf probs."
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-28
I am experimenting with  kernel 2.6.34-020634rc5-generic and the xorge.edgers.ppa driver updates as described here:
[http://ubuntuforums.org/showpost.php?p=7773102&postcount=1](http://ubuntuforums.org/showpost.php?p=7773102&postcount=1)

I thought it might solve my ATI, KMS and Plymouth problems and to a large extent it has!
But of course new issues have arrisen!
1 - xorg.edgers uses a file: /etc/modprobe.d/radeon-kms.conf
which has the following in it: options radeon modeset=1
I also added options radeon modeset=1 dynpm=1 to enable dynamic power management.

However, doing this does not give the 'correct' output from: dmesg | grep drm
*"[drm] radeon: dynamic power management enabled"* is missing.
"*[drm] radeon: power management initialized" is there.*
I eventually deleted radeon-kms.conf and went back to adding radeon.dynpm=1 to the grub boot options - it worked. radeon.modeset=1 seems to have no effect so I don't use it anywhere.
Any thoughts on that?

2- System will not shutdown correctly
The system reboots ok but does not completely shutdown.
Everything seems to poweroff and you can hear things spinning down but  the Plymouth splash with the animated dots is still on the screen.

This is the biggest remaining problem,only affects the 2.6.34 kernel in my case, others are suffering here:
[http://ubuntuforums.org/showthread.php?t=1445140](http://ubuntuforums.org/showthread.php?t=1445140)
But I think they may be using standard kernels?

Edit - to shut down I am rebooting, when back at grub, press c then type halt at the prompt.

---

### Post by BrokeMahPC on 2010-04-28
Out put of
```
dmesg | grep drm
```

```
$ dmesg | grep drm
[    2.011170] [drm] Initialized drm 1.1.0 20060810
[    2.382389] [drm] radeon defaulting to kernel modesetting.
[    2.382392] [drm] radeon kernel modesetting enabled.
[    2.383373] [drm] initializing kernel modesetting (RV730 0x1002:0x9490).
[    2.383464] [drm] register mmio base: 0xFE8E0000
[    2.383465] [drm] register mmio size: 65536
[    2.383594] [drm] Clocks initialized !
[    2.383597] [drm] Internal thermal controller with fan control
[    2.383599] [drm] 4 Power State(s)
[    2.383601] [drm] State 0 Default (default)
[    2.383602] [drm]     16 PCIE Lanes
[    2.383603] [drm]     3 Clock Mode(s)
[    2.383605] [drm]         0 engine/memory: 750000/1000000
[    2.383606] [drm]         1 engine/memory: 750000/1000000
[    2.383608] [drm]         2 engine/memory: 750000/1000000
[    2.383610] [drm] State 1 Performance 
[    2.383611] [drm]     16 PCIE Lanes
[    2.383612] [drm]     3 Clock Mode(s)
[    2.383614] [drm]         0 engine/memory: 500000/750000
[    2.383615] [drm]         1 engine/memory: 500000/750000
[    2.383617] [drm]         2 engine/memory: 750000/1000000
[    2.383618] [drm] State 2 Default 
[    2.383620] [drm]     16 PCIE Lanes
[    2.383621] [drm]     3 Clock Mode(s)
[    2.383622] [drm]         0 engine/memory: 750000/1000000
[    2.383624] [drm]         1 engine/memory: 750000/1000000
[    2.383625] [drm]         2 engine/memory: 750000/1000000
[    2.383627] [drm] State 3 Performance 
[    2.383628] [drm]     16 PCIE Lanes
[    2.383629] [drm]     3 Clock Mode(s)
[    2.383631] [drm]         0 engine/memory: 500000/750000
[    2.383632] [drm]         1 engine/memory: 500000/750000
[    2.383634] [drm]         2 engine/memory: 750000/1000000
[    2.383639] [drm] radeon: dynamic power management enabled
[    2.383640] [drm] radeon: power management initialized
[    2.384550] [drm] Detected VRAM RAM=256M, BAR=256M
[    2.384553] [drm] RAM width 128bits DDR
[    2.384632] [drm] radeon: 256M of VRAM memory ready
[    2.384633] [drm] radeon: 512M of GTT memory ready.
[    2.384703] [drm] radeon: using MSI.
[    2.384731] [drm] radeon: irq initialized.
[    2.384733] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.385160] [drm] Loading RV730 Microcode
[    2.466293] [drm] ring test succeeded in 1 usecs
[    2.466413] [drm] radeon: ib pool ready.
[    2.466476] [drm] ib test succeeded in 0 usecs
[    2.466478] [drm] Enabling audio support
[    2.466498] [drm] Default TV standard: PAL
[    2.466555] [drm] Default TV standard: PAL
[    2.466575] [drm] Default TV standard: PAL
[    2.466608] [drm] Radeon Display Connectors
[    2.466610] [drm] Connector 0:
[    2.466611] [drm]   DVI-I
[    2.466612] [drm]   HPD2
[    2.466614] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    2.466616] [drm]   Encoders:
[    2.466617] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    2.466618] [drm]     DFP2: INTERNAL_UNIPHY1
[    2.466620] [drm] Connector 1:
[    2.466621] [drm]   DIN
[    2.466622] [drm]   Encoders:
[    2.466623] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[    2.466625] [drm] Connector 2:
[    2.466626] [drm]   DVI-I
[    2.466627] [drm]   HPD1
[    2.466629] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[    2.466630] [drm]   Encoders:
[    2.466631] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.466633] [drm]     DFP1: INTERNAL_UNIPHY
[    2.520965] [drm] Requested: e: 50000 m: 75000 p: 16
[    2.520968] [drm] Setting: e: 50000 m: 75000 p: 16
[    2.600579] [drm] fb mappable at 0xD0141000
[    2.600581] [drm] vram apper at 0xD0000000
[    2.600583] [drm] size 8294400
[    2.600584] [drm] fb depth is 24
[    2.600585] [drm]    pitch is 7680
[    2.600640] fb0: radeondrmfb frame buffer device
[    2.600647] [drm] Initialized radeon 2.3.0 20080528 for 0000:01:00.0 on minor 0
[    2.605456] [drm] Requested: e: 75000 m: 100000 p: 16
[    2.605458] [drm] Setting: e: 75000 m: 100000 p: 16
[    3.204521] [drm] Requested: e: 50000 m: 75000 p: 16
[    3.204525] [drm] Setting: e: 50000 m: 75000 p: 16
[    3.205601] [drm] not in vbl for pm change 00020002 00000000 at entry
```

---

### Post by Killigrew on 2010-04-28
Hi

i have the same shutdown problem.
radeon.conf is working fine for me but i get some slight flickering once in a while if i enable dynpm.

greetings

---

