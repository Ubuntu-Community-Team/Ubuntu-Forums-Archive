---
title: "Firefox + UIM + Flash = Crashes"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vivia on 2009-10-14
Hello,

My Firefox crashes almost every time I try to stop a flash movie that's playing before it ends (for example, I decide this YouTube video isn't interesting). I tried export LD_PRELOAD=/usr/lib/libGL.so.1 and export XLIB_SKIP_ARGB_VISUALS=1 but nothing changes. I ran it on gdb and found this backtrace:

```
Program received signal SIGSEGV, Segmentation fault.
0x008f0072 in g_type_check_instance_cast () from /usr/lib/libgobject-2.0.so.0
(gdb) bt full
#0  0x008f0072 in g_type_check_instance_cast ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#1  0x064c0f22 in ?? () from /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so
No symbol table info available.
#2  0x064c1b55 in ?? () from /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so
No symbol table info available.
#3  0x064c1c31 in ?? () from /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so
No symbol table info available.
#4  0x07328394 in gtk_im_context_focus_in () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0x07328394 in gtk_im_context_focus_in () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0x01651f3b in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
No symbol table info available.
#7  0x01657945 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
No symbol table info available.
#8  0x01312716 in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
No symbol table info available.
#9  0x01091f5e in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
No symbol table info available.
#10 0x0109245d in ?? () from /usr/lib/xulrunner-1.9.1.3/libxul.so
No symbol table info available.
```

Not sure how to proceed, not sure whether the bug is in Firefox, Flash, UIM (yes I do need it) or some gtk library.

Any suggestions?

---

### Post by areteichi on 2009-10-16
I'm not sure if I had the same problem as you, but firefox in ubuntu 9.10 seems much more stable after I switched the input system to ibus. Unless there is a particular reason for you to use uim, why not give ibus a try?

---

