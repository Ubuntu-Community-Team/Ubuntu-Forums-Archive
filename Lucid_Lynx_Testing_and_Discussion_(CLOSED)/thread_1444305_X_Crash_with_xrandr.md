---
title: "X Crash with xrandr"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by coutts99 on 2010-04-01
Trying to use multiple monitors with KDE4.

When using system settings or xrandr on the command line, X restarts when I enable multiple monitors.

Anyone else getting this?

---

### Post by coutts99 on 2010-04-09
I get the following in my Xorg log -:

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xf17410]
3: /usr/lib/dri/i915_dri.so (0xff8000+0x20a336) [0x1202336]
4: /usr/lib/dri/i915_dri.so (_mesa_execute_program+0x2a2d) [0x113f08d]
5: /usr/lib/dri/i915_dri.so (_swrast_exec_fragment_program+0x1a4) [0x12025d4]
6: /usr/lib/dri/i915_dri.so (0xff8000+0x1662ff) [0x115e2ff]
7: /usr/lib/dri/i915_dri.so (_swrast_write_rgba_span+0x1030) [0x115fa10]
8: /usr/lib/dri/i915_dri.so (0xff8000+0x180442) [0x1178442]
9: /usr/lib/dri/i915_dri.so (0xff8000+0x159d2f) [0x1151d2f]
10: /usr/lib/dri/i915_dri.so (_swrast_Triangle+0x2d) [0x1150f3d]
11: /usr/lib/dri/i915_dri.so (0xff8000+0x18cc1f) [0x1184c1f]
12: /usr/lib/dri/i915_dri.so (0xff8000+0x18cc65) [0x1184c65]
13: /usr/lib/dri/i915_dri.so (0xff8000+0x125327) [0x111d327]
14: /usr/lib/dri/i915_dri.so (0xff8000+0x126979) [0x111e979]
15: /usr/lib/dri/i915_dri.so (_tnl_run_pipeline+0x163) [0x1112673]
16: /usr/lib/dri/i915_dri.so (0xff8000+0x7195d) [0x106995d]
17: /usr/lib/dri/i915_dri.so (_tnl_draw_prims+0xc76) [0x11133c6]
18: /usr/lib/dri/i915_dri.so (_tnl_vbo_draw_prims+0x79) [0x1113829]
19: /usr/lib/dri/i915_dri.so (vbo_exec_vtx_flush+0x5f4) [0x110b844]
20: /usr/lib/dri/i915_dri.so (vbo_exec_FlushVertices_internal+0x3a) [0x110760a]
21: /usr/lib/dri/i915_dri.so (vbo_exec_FlushVertices+0x50) [0x11076c0]
22: /usr/lib/dri/i915_dri.so (_mesa_MatrixMode+0x181) [0x10cc1d1]
23: /usr/lib/xorg/modules/extensions/libglx.so (0x5b2000+0x8d19) [0x5bad19]
24: /usr/lib/xorg/modules/extensions/libglx.so (0x5b2000+0x323c4) [0x5e43c4]
25: /usr/lib/xorg/modules/extensions/libglx.so (0x5b2000+0x36d12) [0x5e8d12]
26: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
27: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
28: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x3eabd6]
29: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

---

### Post by coutts99 on 2010-04-09
Created bug report if anyone is interested -:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/559039](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/559039)

---

