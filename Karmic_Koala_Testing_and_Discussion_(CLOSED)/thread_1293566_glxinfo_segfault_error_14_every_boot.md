---
title: "glxinfo segfault error 14 every boot"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by null_pointer_us on 2009-10-17
I just checked out my dmesg output after startup and found the following lines:

```
[   16.360243] [drm] Initialized drm 1.1.0 20060810
[   16.389382] [drm] Initialized vboxvideo 1.0.0 20090303 for 0000:00:02.0 on minor 0
[   22.758144] glxinfo[1449]: segfault at 21 ip 0000000000000021 sp 0000000001e07750 error 14 in glxinfo[400000+5000]

```

This happens every boot. Sometimes I also get an error message in gnome about glxinfo closing unexpectedly, but usually it's just a silent failure.

Everything on the desktop seems to work fine (even compiz).

BTW, I do rebuild the vbox guest additions after every kernel upgrade.

---

### Post by null_pointer_us on 2009-10-20
I subscribed to [bug report 403727]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/403727").

EDIT 1: Nevermind about the keyserver, it just had lots of timeouts before it finally succeeded.

EDIT 2: GDB says it cannot find debugging symbols for glxinfo.

Oddly, installing these packages:

[LIST]
[*]libgl1-mesa-dri-dbg
[*]libgl1-mesa-glx-dbg
[/LIST]
...or these packages:

[LIST]
[*]libgl1-mesa-dri-dbgsym
[*]libgl1-mesa-glx-dbgsym
[*]libglu1-mesa-dbgsym
[*]mesa-utils-dbgsym
[/LIST]
...or this package:

[LIST]
[*]mesa-utils-dbgsym
[/LIST]
...does NOT enable gdb to locate debugging symbols for glxinfo. :confused:

So the backtrace I obtained is useless, ATM.

---

