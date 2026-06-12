---
title: "GNOME System Monitor not starting on Ubuntu 10.10"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by million on 2011-01-29
Hi,

I'm using Ubuntu 10.10 server edition on AMD 64-bit machine. When I try to open system monitor(system->administration->system monitor) it's not starting. Then i use console to open system monitor using command #gnome-

system-monitor then it gave me the following error on the console.

==============================================


** (gnome-system-monitor:19279): WARNING **: SELinux was found but is not enabled.

*** glibc detected *** gnome-system-monitor: malloc(): memory corruption: 0x0000000000881d80 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f1ec27054b6]
/lib/libc.so.6(+0x7b55f)[0x7f1ec270955f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7f1ec270a38e]
/usr/lib/libpixman-1.so.0(+0x1724b)[0x7f1ebe5c724b]
/usr/lib/libpixman-1.so.0(pixman_image_create_solid_fill+0x9)[0x7f1ebe5e88b9]
/usr/lib/libpixman-1.so.0(pixman_image_fill_boxes+0x23a)[0x7f1ebe5e263a]
/usr/lib/libcairo.so.2(+0x27c68)[0x7f1ec457bc68]
/usr/lib/libcairo.so.2(+0x48848)[0x7f1ec459c848]
/usr/lib/libcairo.so.2(+0x4b885)[0x7f1ec459f885]
/usr/lib/libcairo.so.2(+0x48861)[0x7f1ec459c861]
/usr/lib/libcairo.so.2(+0x4cac7)[0x7f1ec45a0ac7]
/usr/lib/libcairo.so.2(+0x4cc92)[0x7f1ec45a0c92]
/usr/lib/libcairo.so.2(+0x4d8d9)[0x7f1ec45a18d9]
/usr/lib/libcairo.so.2(+0x4a191)[0x7f1ec459e191]
/usr/lib/libcairo.so.2(+0x2282a)[0x7f1ec457682a]
/usr/lib/libcairo.so.2(cairo_stroke_preserve+0x1b)[0x7f1ec456d49b]
/usr/lib/libcairo.so.2(cairo_stroke+0x9)[0x7f1ec456d4c9]
gnome-system-monitor[0x415b9d]
gnome-system-monitor[0x4160ee]
/usr/lib/libgtk-x11-2.0.so.0(+0x13a9d8)[0x7f1ec53989d8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f1ec34a0a6e]
/usr/lib/libgobject-2.0.so.0(+0x244d7)[0x7f1ec34b64d7]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x62b)[0x7f1ec34b77db]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f1ec34b7f53]
/usr/lib/libgtk-x11-2.0.so.0(+0x2536df)[0x7f1ec54b16df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x556)[0x7f1ec53921b6]
/usr/lib/libgdk-x11-2.0.so.0(+0x439da)[0x7f1ec4ff29da]
/usr/lib/libgdk-x11-2.0.so.0(+0x43987)[0x7f1ec4ff2987]
/usr/lib/libgdk-x11-2.0.so.0(+0x4046b)[0x7f1ec4fef46b]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_updates+0x16d)[0x7f1ec4ff3e0d]
/usr/lib/libgtk-x11-2.0.so.0(+0x26a2bf)[0x7f1ec54c82bf]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f1ec34a0a6e]
/usr/lib/libgobject-2.0.so.0(+0x24120)[0x7f1ec34b6120]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7e6)[0x7f1ec34b7996]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f1ec34b7f53]
/usr/lib/libgtk-x11-2.0.so.0(+0xb4f70)[0x7f1ec5312f70]
/usr/lib/libgdk-x11-2.0.so.0(+0x1d626)[0x7f1ec4fcc626]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f1ec31f0342]
/lib/libglib-2.0.so.0(+0x442a8)[0x7f1ec31f42a8]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f1ec31f47b5]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f1ec53923e7]
gnome-system-monitor[0x4124d0]
/lib/libc.so.6(__libc_start_main+0xfe)[0x7f1ec26acd8e]
gnome-system-monitor[0x4109d9]
======= Memory map: ========
00400000-0043a000 r-xp 00000000 08:01 8138151                            /usr/bin/gnome-system-monitor
00639000-0063a000 r--p 00039000 08:01 8138151                            /usr/bin/gnome-system-monitor
0063a000-0063c000 rw-p 0003a000 08:01 8138151                            /usr/bin/gnome-system-monitor
0063c000-0063d000 rw-p 00000000 00:00 0 
0064d000-0095c000 rw-p 00000000 00:00 0                                  [heap]
7f1eb3505000-7f1eb35a0000 r--p 00000000 08:01 9175094                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f1eb35a0000-7f1eb35a2000 r-xp 00000000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f1eb35a2000-7f1eb37a1000 ---p 00002000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f1eb37a1000-7f1eb37a2000 r--p 00001000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f1eb37a2000-7f1eb37a3000 rw-p 00002000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f1eb37a3000-7f1eb37b6000 r-xp 00000000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f1eb37b6000-7f1eb39b6000 ---p 00013000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f1eb39b6000-7f1eb39b7000 r--p 00013000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f1eb39b7000-7f1eb39b8000 rw-p 00014000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f1eb39b8000-7f1eb39ba000 r-xp 00000000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f1eb39ba000-7f1eb3bb9000 ---p 00002000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f1eb3bb9000-7f1eb3bba000 r--p 00001000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f1eb3bba000-7f1eb3bbb000 rw-p 00002000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f1eb3bbb000-7f1eb3bbd000 r-xp 00000000 08:01 5244740                    /lib/libutil-2.12.1.so
7f1eb3bbd000-7f1eb3dbc000 ---p 00002000 08:01 5244740                    /lib/libutil-2.12.1.so
7f1eb3dbc000-7f1eb3dbd000 r--p 00001000 08:01 5244740                    /lib/libutil-2.12.1.so
7f1eb3dbd000-7f1eb3dbe000 rw-p 00002000 08:01 5244740                    /lib/libutil-2.12.1.so
7f1eb3dbe000-7f1eb3dfe000 r-xp 00000000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f1eb3dfe000-7f1eb3ffe000 ---p 00040000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f1eb3ffe000-7f1eb3fff000 r--p 00040000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f1eb3fff000-7f1eb4000000 rw-p 00041000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f1eb4000000-7f1eb4021000 rw-p 00000000 00:00 0 
7f1eb4021000-7f1eb8000000 ---p 00000000 00:00 0 
7f1eb801b000-7f1eb8026000 r-xp 00000000 08:01 5242951                    /lib/libudev.so.0.9.1
7f1eb8026000-7f1eb8226000 ---p 0000b000 08:01 5242951                    /lib/libudev.so.0.9.1
7f1eb8226000-7f1eb8227000 r--p 0000b000 08:01 5242951                    /lib/libudev.so.0.9.1
7f1eb8227000-7f1eb8228000 rw-p 0000c000 08:01 5242951                    /lib/libudev.so.0.9.1
7f1eb8228000-7f1eb823e000 r-xp 00000000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f1eb823e000-7f1eb843e000 ---p 00016000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f1eb843e000-7f1eb843f000 r--p 00016000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f1eb843f000-7f1eb8440000 rw-p 00017000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f1eb8440000-7f1eb8468000 r-xp 00000000 08:01 8136071                    /usr/lib/gio/modules/libgvfsdbus.so
7f1eb8468000-7f1eb8668000 ---p 00028000 08:01 8136071                    /usr/lib/gio/modules/libgvfsdbus.so
7f1eb8668000-7f1eb8669000 r--p 00028000 08:01 8136071                    /usr/lib/gio/modules/libgvfsdbus.so
7f1eb8669000-7f1eb866a000 rw-p 00029000 08:01 8136071                    /usr/lib/gio/modules/libgvfsdbus.so
7f1eb866a000-7f1eb9102000 r--p 00000000 08:01 9312355                    /usr/share/icons/hicolor/icon-theme.cache
7f1eb9102000-7f1ebb3ac000 r--p 00000000 08:01 9311082                    /usr/share/icons/gnome/icon-theme.cache
7f1ebb3ac000-7f1ebb3d7000 r-xp 00000000 08:01 9310286                    /usr/lib/gtk-

2.0/2.10.0/engines/libclearlooks.soAborted

===========================================================
I upgrade the kernel version from 23 to 25, but still not working
Please help me to fix this issue.

Thanks

---

### Post by million on 2011-01-29
Hi,

I installed selinux and still following error occur.

---------------------------


*** glibc detected *** gnome-system-monitor: malloc(): memory corruption: 0x0000000000ba47c0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f021af384b6]
/lib/libc.so.6(+0x7b55f)[0x7f021af3c55f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7f021af3d38e]
/usr/lib/libpixman-1.so.0(+0x1724b)[0x7f0216dfa24b]
/usr/lib/libpixman-1.so.0(pixman_image_create_solid_fill+0x9)[0x7f0216e1b8b9]
/usr/lib/libpixman-1.so.0(pixman_image_fill_boxes+0x23a)[0x7f0216e1563a]
/usr/lib/libcairo.so.2(+0x27c68)[0x7f021cdaec68]
/usr/lib/libcairo.so.2(+0x48848)[0x7f021cdcf848]
/usr/lib/libcairo.so.2(+0x4b885)[0x7f021cdd2885]
/usr/lib/libcairo.so.2(+0x48861)[0x7f021cdcf861]
/usr/lib/libcairo.so.2(+0x4cac7)[0x7f021cdd3ac7]
/usr/lib/libcairo.so.2(+0x4cc92)[0x7f021cdd3c92]
/usr/lib/libcairo.so.2(+0x4d8d9)[0x7f021cdd48d9]
/usr/lib/libcairo.so.2(+0x4a191)[0x7f021cdd1191]
/usr/lib/libcairo.so.2(+0x2282a)[0x7f021cda982a]
/usr/lib/libcairo.so.2(cairo_stroke_preserve+0x1b)[0x7f021cda049b]
/usr/lib/libcairo.so.2(cairo_stroke+0x9)[0x7f021cda04c9]
gnome-system-monitor[0x415b9d]
gnome-system-monitor[0x4160ee]
/usr/lib/libgtk-x11-2.0.so.0(+0x13a9d8)[0x7f021dbcb9d8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f021bcd3a6e]
/usr/lib/libgobject-2.0.so.0(+0x244d7)[0x7f021bce94d7]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x62b)[0x7f021bcea7db]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f021bceaf53]
/usr/lib/libgtk-x11-2.0.so.0(+0x2536df)[0x7f021dce46df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x556)[0x7f021dbc51b6]
/usr/lib/libgdk-x11-2.0.so.0(+0x439da)[0x7f021d8259da]
/usr/lib/libgdk-x11-2.0.so.0(+0x43987)[0x7f021d825987]
/usr/lib/libgdk-x11-2.0.so.0(+0x4046b)[0x7f021d82246b]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_updates+0x16d)[0x7f021d826e0d]
/usr/lib/libgtk-x11-2.0.so.0(+0x26a2bf)[0x7f021dcfb2bf]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f021bcd3a6e]
/usr/lib/libgobject-2.0.so.0(+0x24120)[0x7f021bce9120]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7e6)[0x7f021bcea996]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f021bceaf53]
/usr/lib/libgtk-x11-2.0.so.0(+0xb4f70)[0x7f021db45f70]
/usr/lib/libgdk-x11-2.0.so.0(+0x1d626)[0x7f021d7ff626]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f021ba23342]
/lib/libglib-2.0.so.0(+0x442a8)[0x7f021ba272a8]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f021ba277b5]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f021dbc53e7]
gnome-system-monitor[0x4124d0]
/lib/libc.so.6(__libc_start_main+0xfe)[0x7f021aedfd8e]
gnome-system-monitor[0x4109d9]
======= Memory map: ========
00400000-0043a000 r-xp 00000000 08:01 8138151                            /usr/bin/gnome-system-monitor
00639000-0063a000 r--p 00039000 08:01 8138151                            /usr/bin/gnome-system-monitor
0063a000-0063c000 rw-p 0003a000 08:01 8138151                            /usr/bin/gnome-system-monitor
0063c000-0063d000 rw-p 00000000 00:00 0 
00978000-00c8d000 rw-p 00000000 00:00 0                                  [heap]
7f020b9f2000-7f020b9f4000 r-xp 00000000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f020b9f4000-7f020bbf3000 ---p 00002000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f020bbf3000-7f020bbf4000 r--p 00001000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f020bbf4000-7f020bbf5000 rw-p 00002000 08:01 8144865                    /usr/lib/gconv/ISO8859-1.so
7f020bbf5000-7f020bbf7000 r-xp 00000000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f020bbf7000-7f020bdf6000 ---p 00002000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f020bdf6000-7f020bdf7000 r--p 00001000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f020bdf7000-7f020bdf8000 rw-p 00002000 08:01 9306138                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f020bdf8000-7f020bdff000 r-xp 00000000 08:01 8141428                    /usr/lib/gio/modules/libdconfsettings.so
7f020bdff000-7f020bffe000 ---p 00007000 08:01 8141428                    /usr/lib/gio/modules/libdconfsettings.so
7f020bffe000-7f020bfff000 r--p 00006000 08:01 8141428                    /usr/lib/gio/modules/libdconfsettings.so
7f020bfff000-7f020c000000 rw-p 00007000 08:01 8141428                    /usr/lib/gio/modules/libdconfsettings.so
7f020c000000-7f020c021000 rw-p 00000000 00:00 0 
7f020c021000-7f0210000000 ---p 00000000 00:00 0 
7f0210159000-7f02101f4000 r--p 00000000 08:01 9175094                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f02101f4000-7f0210207000 r-xp 00000000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f0210207000-7f0210407000 ---p 00013000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f0210407000-7f0210408000 r--p 00013000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f0210408000-7f0210409000 rw-p 00014000 08:01 8136072                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f0210409000-7f021040b000 r-xp 00000000 08:01 5244740                    /lib/libutil-2.12.1.so
7f021040b000-7f021060a000 ---p 00002000 08:01 5244740                    /lib/libutil-2.12.1.so
7f021060a000-7f021060b000 r--p 00001000 08:01 5244740                    /lib/libutil-2.12.1.so
7f021060b000-7f021060c000 rw-p 00002000 08:01 5244740                    /lib/libutil-2.12.1.so
7f021060c000-7f0210617000 r-xp 00000000 08:01 5242951                    /lib/libudev.so.0.9.1
7f0210617000-7f0210817000 ---p 0000b000 08:01 5242951                    /lib/libudev.so.0.9.1
7f0210817000-7f0210818000 r--p 0000b000 08:01 5242951                    /lib/libudev.so.0.9.1
7f0210818000-7f0210819000 rw-p 0000c000 08:01 5242951                    /lib/libudev.so.0.9.1
7f0210819000-7f0210859000 r-xp 00000000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f0210859000-7f0210a59000 ---p 00040000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f0210a59000-7f0210a5a000 r--p 00040000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f0210a5a000-7f0210a5b000 rw-p 00041000 08:01 5243001                    /lib/libdbus-1.so.3.5.2
7f0210a5b000-7f0210a71000 r-xp 00000000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f0210a71000-7f0210c71000 ---p 00016000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f0210c71000-7f0210c72000 r--p 00016000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f0210c72000-7f0210c73000 rw-p 00017000 08:01 8136067                    /usr/lib/libgvfscommon.so.0.0.0
7f0210c73000-7f0210c9b000 r-xp 00000000 08:01 8136071                    /usr/lib/gio/modules/libgvfsdbus.so
7f0210c9b000-7f0210e9b000 ---p 00028000 08:01 8136071                    /usr/lib/gio/modules/libgvfsdbus.soAborted

Please help me to fix this issue.

Thanks

---

### Post by DaveWut on 2011-02-12
Hi guys,
I have the same exact problem when Im remotely connected with xrdp. Can you guys help us?

Thanks!

---

