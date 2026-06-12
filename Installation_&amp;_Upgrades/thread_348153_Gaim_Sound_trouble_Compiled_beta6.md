---
title: "Gaim Sound trouble Compiled beta6"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Drezliok on 2007-01-28
I compiled  Gaim 2.0.0 Beta6 I got the SSL to work for MSN But I have no sound options other than
Console Beep
No Sound
Command

When I set it to Command and use ALSA, OSS. Or NAS, ARTs, ESD it crashes on me and crashes. 

I ran gaim from my terminal and this is the output from the crash.

```
drezliok@TuxEater:~$ gaim
*** glibc detected *** gaim: double free or corruption (fasttop): 0x085c7060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74788bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7478a44]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7702b51]
gaim[0x80cae2d]
/usr/local/lib/libgaim.so.0(gaim_sound_play_file+0x37)[0xb7811ce7]
gaim[0x80cacef]
/usr/local/lib/libgaim.so.0(gaim_sound_play_event+0x78)[0xb7811ca8]
gaim[0x80cb341]
/usr/local/lib/libgaim.so.0(gaim_marshal_VOID__POINTER_POINTER_POINTER+0x26)[0xb780af46]
/usr/local/lib/libgaim.so.0(gaim_signal_emit_vargs+0xa9)[0xb780b779]
/usr/local/lib/libgaim.so.0(gaim_signal_emit+0x3c)[0xb780b88c]
/usr/local/lib/libgaim.so.0[0xb77e848c]
gaim[0x8088134]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb7795b29]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb778879b]
/usr/lib/libgobject-2.0.so.0[0xb7798e81]
/usr/lib/libgobject-2.0.so.0(g_signal_emitv+0x198)[0xb779a418]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bde41b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bde7c8]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bde99b]
/usr/lib/libgtk-x11-2.0.so.0(gtk_bindings_activate_event+0xd9)[0xb7bdeab9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dd0ab8]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d7215b]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7cb1b00]
/usr/lib/libgobject-2.0.so.0[0xb7786fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20d)[0xb778887d]
/usr/lib/libgobject-2.0.so.0[0xb77991e3]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb7799e7f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb779a279]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dc55f8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_window_propagate_key_event+0x107)[0xb7dd5677]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dd86dc]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7cb1b00]
/usr/lib/libgobject-2.0.so.0[0xb7786fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb778879b]
/usr/lib/libgobject-2.0.so.0[0xb77991e3]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb7799e7f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb779a279]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dc55f8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x1ba)[0xb7caaf2a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x317)[0xb7cac0f7]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b357ea]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb76fb802]
/usr/lib/libglib-2.0.so.0[0xb76fe7df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb76feb89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cac574]
gaim(main+0x936)[0x80adc26]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb74278cc]
gaim(gtk_widget_grab_focus+0x39)[0x8067171]
======= Memory map: ========
08048000-080e9000 r-xp 00000000 08:01 2725685    /usr/local/bin/gaim
080e9000-080ec000 rw-p 000a0000 08:01 2725685    /usr/local/bin/gaim
080ec000-085e0000 rw-p 080ec000 00:00 0          [heap]
b3600000-b3621000 rw-p b3600000 00:00 0 
b3621000-b3700000 ---p b3621000 00:00 0 
b3747000-b3751000 r-xp 00000000 08:01 1860496    /lib/libgcc_s.so.1
b3751000-b3752000 rw-p 00009000 08:01 1860496    /lib/libgcc_s.so.1
b3760000-b37c0000 rw-s 00000000 00:08 1310743    /SYSV00000000 (deleted)
b37c0000-b3824000 r--p 00000000 08:01 2743948    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b3824000-b3884000 rw-s 00000000 00:08 1277974    /SYSV00000000 (deleted)
b3884000-b3889000 r-xp 00000000 08:01 2791427    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3889000-b388a000 rw-p 00004000 08:01 2791427    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3892000-b38fe000 r--p 00000000 08:01 2743945    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b38fe000-b3a7d000 r--p 00000000 08:01 2839892    /usr/share/icons/hicolor/icon-theme.cache
b3a7d000-b3bfc000 r--p 00000000 08:01 2839892    /usr/share/icons/hicolor/icon-theme.cache
b3bfc000-b4ce4000 r--p 00000000 08:01 2795463    /usr/share/icons/crystalsvg/icon-theme.cache
b4ce4000-b5dcc000 r--p 00000000 08:01 2795463    /usr/share/icons/crystalsvg/icon-theme.cache
b5dcc000-b641d000 r--p 00000000 08:01 2845307    /usr/share/icons/gnome/icon-theme.cache
b641d000-b6a6e000 r--p 00000000 08:01 2845307    /usr/share/icons/gnome/icon-theme.cache
b6a6e000-b6cc6000 r--p 00000000 08:01 2974624    /usr/share/icons/Tango/icon-theme.cache
b6cc6000-b6f1e000 r--p 00000000 08:01 2974624    /usr/share/icons/Tango/icon-theme.cache
b6f1e000-b6f20000 r-xp 00000000 08:01 2791624    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6f20000-b6f21000 rw-p 00001000 08:01 2791624    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6f210Aborted (core dumped)

```


Other than the sound issue it seems to run fine.

[PS This is the first program I compiled with out copy/pasting from a tutorial so I could have missed something in the compile and not know it.]

---

