---
title: "X crashing, log inside."
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-10-03
Hi folks, X has crashed 3 times today after upgrading some stuff. I also followed [the pulseaudio howto]("http://ubuntuforums.org/showthread.php?t=866965") today, but I don't think that is related to the crash. 

Some 'maybe you're guilty' packages:

```
[UPGRADE] x11-common 1:7.4~2ubuntu4 -> 1:7.4~2ubuntu5
[UPGRADE] xbase-clients 1:7.4~2ubuntu4 -> 1:7.4~2ubuntu5
[UPGRADE] xorg 1:7.4~2ubuntu4 -> 1:7.4~2ubuntu5
[UPGRADE] xserver-xorg 1:7.4~2ubuntu4 -> 1:7.4~2ubuntu5
[UPGRADE] xserver-xorg-input-all 1:7.4~2ubuntu4 -> 1:7.4~2ubuntu5
[UPGRADE] xserver-xorg-video-all 1:7.4~2ubuntu4 -> 1:7.4~2ubuntu5

```

The Backtrace in the X log:

```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3069]
1: [0xb7fc2400]
2: /usr/lib/dri/r300_dri.so(_mesa_update_texture+0x2ab) [0xad6378cb]
3: /usr/lib/dri/r300_dri.so(_mesa_update_state_locked+0x729) [0xad620019]
4: /usr/lib/dri/r300_dri.so(_mesa_update_state+0x2a) [0xad62020a]
5: /usr/lib/dri/r300_dri.so(_mesa_GetIntegerv+0x278) [0xad6f55f8]
6: /usr/lib/xorg/modules/extensions//libglx.so [0xb7aee541]
7: /usr/lib/xorg/modules/extensions//libglx.so [0xb7ae0368]
8: /usr/lib/xorg/modules/extensions//libglx.so [0xb7adf227]
9: /usr/lib/xorg/modules/extensions//libglx.so [0xb7ae3d8a]
10: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c91f]
11: /usr/X11R6/bin/X(main+0x47d) [0x8071d8d]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7bc4685]
13: /usr/X11R6/bin/X [0x8071171]
Saw signal 11.  Server aborting.

```

My xorg.conf is:

```
Section "Device"
        Identifier      "Configured Video Device"
#       Driver "radeonhd"
  Option                "AccelMethod"   "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

