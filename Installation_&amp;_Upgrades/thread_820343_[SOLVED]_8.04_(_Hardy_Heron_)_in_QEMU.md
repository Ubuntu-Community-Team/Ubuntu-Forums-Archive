---
title: "[SOLVED] 8.04 ( Hardy Heron ) in QEMU"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2008-06-06
Just leaving a quick note in case others come here trying to find out why Xorg won't start in QEMU ( when doing a manual Xorg install from a minimal installation specifically ).

Either the Linux Cirrus driver or QEMU's emulation of the hardware doesn't support 32bpp and/or returns incorrect data to DDC(DCC?) probing during auto-configuration. The fix I have found which works for me is a simple line added to xorg.conf which overrides the auto-configuration.

> Section "Screen"
*...existing lines...*
DefaultDepth 16
EndSection

Setting it to 24 may also work, but I did not try it. I have already read that passing the '-std-vga' parameter to qemu also resolves the issue by changing the emulated hardware ( I presume it supports 32bpp ) but again, I have not tried it.

Hope this helps

---

