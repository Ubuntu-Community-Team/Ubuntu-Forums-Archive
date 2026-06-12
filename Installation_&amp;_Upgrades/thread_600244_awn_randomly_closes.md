---
title: "awn randomly closes"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by Villenya on 2007-11-02
i just got awn recently and it would randomly disappear without any error messages.
I haven't noticed any consistancy so i have no idea what's causing it.

anyone got any ideas?

---

### Post by Villenya on 2007-11-03
i did gdb and backtrace and got:

** (avant-window-navigator:6716): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6716): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1226627408 (LWP 6716)]
0xb733681a in sem_post@GLIBC_2.0 () from /lib/tls/i686/cmov/libpthread.so.0
(gdb) bt
#0  0xb733681a in sem_post@GLIBC_2.0 () from /lib/tls/i686/cmov/libpthread.so.0
#1  0xb7354e82 in awn_shared_unlock () at awn-shared.c:90
#2  0x08052656 in resize (window=0x80bd830) at awn-bar.c:784
#3  0xb74908d6 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0x080bd830 in ?? ()
#5  0xb73338ac in __pthread_mutex_unlock_usercnt ()
   from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb749011c in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#7  0xb749355f in ?? () from /usr/lib/libglib-2.0.so.0
#8  0x0808b500 in ?? ()
#9  0x00000000 in ?? ()


bump?

---

