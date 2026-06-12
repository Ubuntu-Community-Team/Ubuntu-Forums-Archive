---
title: "system is extremely unstable since feisty beta"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by katana2k on 2007-05-23
my system has never been unstable with ubuntu until a month or so before feisty released and i was using the beta and its been extremely unstable since then. 

many applications close themselves without warning with output like: 

Thunar
```
jeff@cybertron:~$ thunar
thunar: /build/buildd/libcairo-1.4.2/src/cairo.c:256: cairo_destroy: Assertion `cr->ref_count > 0' failed.
Aborted (core dumped)

```

Gajim
```
jeff@cybertron:~$ gajim
/usr/share/gajim/src/systray.py:35: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon as trayicon       # gnomepythonextras trayicon
gajim: /build/buildd/libcairo-1.4.2/src/cairo.c:256: cairo_destroy: Assertion `cr->ref_count > 0' failed.
Aborted (core dumped)
```

Network Manager Applet
```
jeff@cybertron:~$ nm-applet
*** glibc detected *** nm-applet: corrupted double-linked list: 0x08253b58 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb716abbb]
/lib/tls/i686/cmov/libc.so.6[0xb716ce38]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb716e60e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb727b2c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb767fdb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb76811e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_region_intersect+0x6e)[0xb7951c6e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x12d)[0xb77a2d4d]
/usr/lib/libgtk-x11-2.0.so.0[0xb77a2df1]
/usr/lib/libgtk-x11-2.0.so.0[0xb7846109]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb77a37db]
/usr/lib/libgtk-x11-2.0.so.0[0xb77a38cf]
/usr/lib/libgtk-x11-2.0.so.0[0xb78403e2]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb78396b0]
/usr/lib/libgobject-2.0.so.0[0xb72e3e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb72e562b]
/usr/lib/libgobject-2.0.so.0[0xb72f6753]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb72f73ef]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb72f77e9]
/usr/lib/libgtk-x11-2.0.so.0[0xb794de18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x534)[0xb7833de4]
/usr/lib/libgdk-x11-2.0.so.0[0xb768464f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0x97)[0xb7684887]
/usr/lib/libgdk-x11-2.0.so.0[0xb7684905]
/usr/lib/libglib-2.0.so.0[0xb7272091]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7273df2]
/usr/lib/libglib-2.0.so.0[0xb7276dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7277179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7834044]
nm-applet(main+0x121)[0x8052311]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb711aebc]
nm-applet[0x8052161]
======= Memory map: ========
08048000-08071000 r-xp 00000000 08:01 4571854    /usr/bin/nm-applet
08071000-08072000 rw-p 00029000 08:01 4571854    /usr/bin/nm-applet
08072000-0825f000 rw-p 08072000 00:00 0          [heap]
b5e00000-b5e21000 rw-p b5e00000 00:00 0 
b5e21000-b5f00000 ---p b5e21000 00:00 0 
b5fe8000-b5ff3000 r-xp 00000000 08:01 9273408    /lib/libgcc_s.so.1
b5ff3000-b5ff4000 rw-p 0000a000 08:01 9273408    /lib/libgcc_s.so.1
b6000000-b6002000 r-xp 00000000 08:01 4703419    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6002000-b6003000 rw-p 00001000 08:01 4703419    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6003000-b6080000 r--p 00000000 08:01 4833412    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6080000-b6086000 r--s 00000000 08:01 5423183    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6086000-b6087000 r--s 00000000 08:01 5423211    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6087000-b608a000 r--s 00000000 08:01 5423199    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b608a000-b608b000 r--s 00000000 08:01 5423205    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b608b000-b608c000 r--s 00000000 08:01 5423186    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b608c000-b6090000 r--s 00000000 08:01 5423180    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6090000-b6091000 r--s 00000000 08:01 5423168    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6091000-b6093000 r--s 00000000 08:01 5423173    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6093000-b6095000 r--s 00000000 08:01 5423161    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6095000-b6096000 r--s 00000000 08:01 5423176    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6096000-b6098000 r--s 00000000 08:01 5423184    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6098000-b609e000 r--s 00000000 08:01 5423174    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b609e000-b60a0000 r--s 00000000 08:01 5423200    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2Aborted (core dumped)
```

XChat
```
jeff@cybertron:~$ xchat
*** glibc detected *** xchat: corrupted double-linked list: 0x08485e90 ***
Killed
```

and so on. my computer also will freeze completely out of nowhere. there is no warning, the system just freezes entirely at random at least once a day. 

if anybody has an idea what i might do to fix this, please let me know :'O

---

### Post by Cimi86 on 2007-05-25
> **katana2k said:**
> my system has never been unstable with ubuntu until a month or so before feisty released and i was using the beta and its been extremely unstable since then. 

many applications close themselves without warning with output like: 

Thunar
```
jeff@cybertron:~$ thunar
thunar: /build/buildd/libcairo-1.4.2/src/cairo.c:256: cairo_destroy: Assertion `cr->ref_count > 0' failed.
Aborted (core dumped)

```

Gajim
```
jeff@cybertron:~$ gajim
/usr/share/gajim/src/systray.py:35: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon as trayicon       # gnomepythonextras trayicon
gajim: /build/buildd/libcairo-1.4.2/src/cairo.c:256: cairo_destroy: Assertion `cr->ref_count > 0' failed.
Aborted (core dumped)
```

Network Manager Applet
```
jeff@cybertron:~$ nm-applet
*** glibc detected *** nm-applet: corrupted double-linked list: 0x08253b58 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb716abbb]
/lib/tls/i686/cmov/libc.so.6[0xb716ce38]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb716e60e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb727b2c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb767fdb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb76811e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_region_intersect+0x6e)[0xb7951c6e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x12d)[0xb77a2d4d]
/usr/lib/libgtk-x11-2.0.so.0[0xb77a2df1]
/usr/lib/libgtk-x11-2.0.so.0[0xb7846109]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb77a37db]
/usr/lib/libgtk-x11-2.0.so.0[0xb77a38cf]
/usr/lib/libgtk-x11-2.0.so.0[0xb78403e2]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb78396b0]
/usr/lib/libgobject-2.0.so.0[0xb72e3e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb72e562b]
/usr/lib/libgobject-2.0.so.0[0xb72f6753]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb72f73ef]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb72f77e9]
/usr/lib/libgtk-x11-2.0.so.0[0xb794de18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x534)[0xb7833de4]
/usr/lib/libgdk-x11-2.0.so.0[0xb768464f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0x97)[0xb7684887]
/usr/lib/libgdk-x11-2.0.so.0[0xb7684905]
/usr/lib/libglib-2.0.so.0[0xb7272091]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7273df2]
/usr/lib/libglib-2.0.so.0[0xb7276dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7277179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7834044]
nm-applet(main+0x121)[0x8052311]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb711aebc]
nm-applet[0x8052161]
======= Memory map: ========
08048000-08071000 r-xp 00000000 08:01 4571854    /usr/bin/nm-applet
08071000-08072000 rw-p 00029000 08:01 4571854    /usr/bin/nm-applet
08072000-0825f000 rw-p 08072000 00:00 0          [heap]
b5e00000-b5e21000 rw-p b5e00000 00:00 0 
b5e21000-b5f00000 ---p b5e21000 00:00 0 
b5fe8000-b5ff3000 r-xp 00000000 08:01 9273408    /lib/libgcc_s.so.1
b5ff3000-b5ff4000 rw-p 0000a000 08:01 9273408    /lib/libgcc_s.so.1
b6000000-b6002000 r-xp 00000000 08:01 4703419    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6002000-b6003000 rw-p 00001000 08:01 4703419    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6003000-b6080000 r--p 00000000 08:01 4833412    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6080000-b6086000 r--s 00000000 08:01 5423183    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6086000-b6087000 r--s 00000000 08:01 5423211    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6087000-b608a000 r--s 00000000 08:01 5423199    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b608a000-b608b000 r--s 00000000 08:01 5423205    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b608b000-b608c000 r--s 00000000 08:01 5423186    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b608c000-b6090000 r--s 00000000 08:01 5423180    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6090000-b6091000 r--s 00000000 08:01 5423168    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6091000-b6093000 r--s 00000000 08:01 5423173    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6093000-b6095000 r--s 00000000 08:01 5423161    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6095000-b6096000 r--s 00000000 08:01 5423176    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6096000-b6098000 r--s 00000000 08:01 5423184    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6098000-b609e000 r--s 00000000 08:01 5423174    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b609e000-b60a0000 r--s 00000000 08:01 5423200    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2Aborted (core dumped)
```

XChat
```
jeff@cybertron:~$ xchat
*** glibc detected *** xchat: corrupted double-linked list: 0x08485e90 ***
Killed
```

and so on. my computer also will freeze completely out of nowhere. there is no warning, the system just freezes entirely at random at least once a day. 

if anybody has an idea what i might do to fix this, please let me know :'O

install murrine 0.53.1, which is not buggied

---

