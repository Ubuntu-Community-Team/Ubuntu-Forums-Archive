---
title: "GTK apps not working..."
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kokopelli on 2009-04-08
Since last night all GTK apps seem to have stopped working.  I can get into KDE fine but if I try and open any GTK app (including Firefox) I get a gray window with a smaller box a lighter shade of gray and then X restarts.

I also can not launch Gnome at all obviously.

In syslog I get this:
```

Apr  8 10:28:40 x200J kernel: [  846.929044] Xorg[4837]: segfault at 20 ip 0000000000496786 sp 00007fff26889160 error 4 in Xor
g[400000+1c3000]
Apr  8 10:28:41 x200J kdm[2934]: X server for display :0 terminated unexpectedly
Apr  8 10:28:41 x200J kernel: [  847.273830] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pip
e 0
Apr  8 10:28:41 x200J kernel: [  847.299846] ksmserver[5175]: segfault at 8 ip 00007f10abe6be2b sp 00007f10a1048888 error 4 in
 libQtDBus.so.4.5.0[7f10abe27000+74000]

```

and this in kdm.log:
```


Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/bin/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7f0e78123040]
3: /lib/libc.so.6(strlen+0x10) [0x7f0e78170c40]
4: /lib/libc.so.6(_IO_vfprintf+0x3dbe) [0x7f0e7813975e]
5: /lib/libc.so.6(__vsnprintf_chk+0xa8) [0x7f0e781ec738]
6: /usr/bin/X(LogVWrite+0x131) [0x4fb4a1]
7: /usr/bin/X(ErrorF+0x8d) [0x4fb68d]
8: /usr/lib64/xorg/modules/input//wacom_drv.so [0x7f0e75f230d2]
9: /usr/bin/X(ActivateDevice+0x3e) [0x447a8e]
10: /usr/bin/X(OpenInputDevice+0x10) [0x4968e0]
11: /usr/bin/X(ProcXOpenDevice+0xa3) [0x545813]
12: /usr/bin/X(Dispatch+0x364) [0x44e304]
13: /usr/bin/X(main+0x3bd) [0x433d8d]
14: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f0e7810e5a6]
15: /usr/bin/X [0x433219]
Saw signal 11.  Server aborting.

```

kern.log:
```

Apr  8 10:28:40 x200J kernel: [  846.929044] Xorg[4837]: segfault at 20 ip 0000000000496786 sp 00007fff26889160 error 4 in Xor
g[400000+1c3000]
Apr  8 10:28:41 x200J kernel: [  847.273830] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pip
e 0
Apr  8 10:28:41 x200J kernel: [  847.299846] ksmserver[5175]: segfault at 8 ip 00007f10abe6be2b sp 00007f10a1048888 error 4 in
 libQtDBus.so.4.5.0[7f10abe27000+74000]
Apr  8 10:28:41 x200J kernel: [  847.597317] wlan0: disassociating by local choice (reason=3)
Apr  8 10:28:42 x200J kernel: [  848.271388] [drm:i915_setparam] *ERROR* unknown parameter 4

```

I did  not notice anything of interest in any of the other logs.  Is anyone else having this problem or any suggestions on how to debug?

---

