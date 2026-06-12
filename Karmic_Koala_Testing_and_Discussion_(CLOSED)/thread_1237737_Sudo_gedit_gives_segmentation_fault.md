---
title: "Sudo gedit gives segmentation fault"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bacardiandwatermelon on 2009-08-11
Hi guys,
I'm having an issue with sudo and gksudo and gedit, I keep getting segmentation faults.. I tried to use gdb, never done it before, so bare with me.. I tried googling but never got anywhere. Any help appreciated.. running wtihout sudo works fine, also running sudo gedit then manually choosing the file works too :-)

```
GNU gdb (GDB) 6.8.50.20090628-cvs-debian
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
(no debugging symbols found)
(gdb) handle SIG33 pass nostop noprint
Signal        Stop    Print    Pass to program    Description
SIG33         No    No    Yes        Real-time event 33
(gdb) set pagination 0
(gdb) run /etc.[K/ssh/ssd[Khd_config
Starting program: /usr/bin/gedit /etc/ssh/sshd_config
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb7aceb70 (LWP 3369)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
0x00c265c2 in g_list_last () from /usr/lib/libglib-2.0.so.0
(gdb) backtrace full
#0  0x00c265c2 in g_list_last () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#1  0x001cd53b in gdk_window_process_updates () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#2  0x008d34c1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#3  0x0041f15c in g_cclosure_marshal_VOID__VOID () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#4  0x00411102 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#5  0x00427ae8 in ?? () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0x00428ecd in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0x00429386 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0x007139d2 in gtk_adjustment_value_changed () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0x008cee74 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0x008d4164 in gtk_text_view_scroll_to_iter () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0x008d42a4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0x008d431a in ?? () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x008d437e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0x001a7098 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#15 0x00c26ec1 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0x00c28c48 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0x00c2c4f0 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#18 0x00c2c95f in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#19 0x007faa49 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0x0806a9ee in main ()
No symbol table info available.
(gdb) info registers
eax            0xaaaaaaaa    -1431655766
ecx            0x80f2068    135209064
edx            0x1    1
ebx            0x23dff4    2351092
esp            0xbfffefd8    0xbfffefd8
ebp            0xbfffefd8    0xbfffefd8
esi            0x83f5738    138368824
edi            0x811c498    135382168
eip            0xc265c2    0xc265c2 <g_list_last+18>
eflags         0x10286    [ PF SF IF RF ]
cs             0x73    115
ss             0x7b    123
ds             0x7b    123
es             0x7b    123
fs             0x0    0
gs             0x33    51
(gdb) thread apply all backtrace

Thread 2 (Thread 0xb7aceb70 (LWP 3369)):
#0  0x0037e422 in __kernel_vsyscall ()
#1  0x00f27142 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x00cc315e in ?? () from /usr/lib/libgthread-2.0.so.0
#3  0x00c03b3c in ?? () from /usr/lib/libglib-2.0.so.0
#4  0x00c546e7 in ?? () from /usr/lib/libglib-2.0.so.0
#5  0x00c5321f in ?? () from /usr/lib/libglib-2.0.so.0
#6  0x00f2280e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x00d9385e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7fe0730 (LWP 3363)):
#0  0x00c265c2 in g_list_last () from /usr/lib/libglib-2.0.so.0
#1  0x001cd53b in gdk_window_process_updates () from /usr/lib/libgdk-x11-2.0.so.0
#2  0x008d34c1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#3  0x0041f15c in g_cclosure_marshal_VOID__VOID () from /usr/lib/libgobject-2.0.so.0
#4  0x00411102 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#5  0x00427ae8 in ?? () from /usr/lib/libgobject-2.0.so.0
#6  0x00428ecd in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#7  0x00429386 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#8  0x007139d2 in gtk_adjustment_value_changed () from /usr/lib/libgtk-x11-2.0.so.0
#9  0x008cee74 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#10 0x008d4164 in gtk_text_view_scroll_to_iter () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x008d42a4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#12 0x008d431a in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x008d437e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x001a7098 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#15 0x00c26ec1 in ?? () from /usr/lib/libglib-2.0.so.0
#16 0x00c28c48 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#17 0x00c2c4f0 in ?? () from /usr/lib/libglib-2.0.so.0
#18 0x00c2c95f in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#19 0x007faa49 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#20 0x0806a9ee in main ()
(gdb) quit
The program is running.  Quit anyway (and kill it)? (y or n) 
```

Oh I think I just found a bug report for it.. Whoops.. Hope it gets fixed soon
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/402225](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/402225)

---

