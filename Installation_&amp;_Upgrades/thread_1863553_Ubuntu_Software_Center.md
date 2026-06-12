---
title: "Ubuntu Software Center"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by jrizeks@gmail.com on 2011-10-17
After Installing the update for 11.10 coming from 11.4 i see a few issues that i am having but all see to be the same problem.  

-1- If i connect any device like (external Hard Drive) it tries to open Ubuntu software, it does mount the hard drive but i do not understand why it opens the software center.
-2- Also in my Launcher if I click in the mount hard drive it tries to open the software center again.

So if anyone have any idea why this is happening, please let me know.

Thank you

---

### Post by jrizeks@gmail.com on 2011-10-18
ok, just realized that now i am not able to open the software center, any ideas?

---

### Post by mado89 on 2011-10-18
I probably do have a similar problem. I also can't start software center
When i lunch it from command line i receive this:

> 2011-10-18 10:23:36,514 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-18 10:23:38,360 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-18 10:23:38,416 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
*** buffer overflow detected ***: /usr/bin/python terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x7f550707c7f7]
/lib/x86_64-linux-gnu/libc.so.6(+0xf7710)[0x7f550707b710]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgr8add_wordEPKciiPtiS1_b+0x7b)[0x7f54e6f173bb]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgr11load_tablesEPKcS1_+0x268)[0x7f54e6f17be8]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgrC1EPKcS1_S1_+0xb2)[0x7f54e6f17d82]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN8HunspellC2EPKcS1_S1_+0x8a)[0x7f54e6f180ba]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN14MySpellChecker17requestDictionaryEPKc+0x39d)[0x7f54e6f254ed]
/usr/local/lib/enchant/libenchant_myspell.so(+0x29656)[0x7f54e6f25656]
/usr/local/lib/libenchant.so.1(+0x41b8)[0x7f54f76911b8]
/usr/local/lib/libenchant.so.1(enchant_broker_request_dict+0xc3)[0x7f54f76925b3]
/usr/lib/libwebkitgtk-3.0.so.0(+0x48cf53)[0x7f54f7d25f53]
/usr/lib/libwebkitgtk-3.0.so.0(+0x4c4bbe)[0x7f54f7d5dbbe]
/usr/lib/libwebkitgtk-3.0.so.0(+0x4c546d)[0x7f54f7d5e46d]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0x513)[0x7f5505bfd373]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x125ac)[0x7f5505bdd5ac]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x294)[0x7f5505bdfe94]
/usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so(+0xbcea)[0x7f5504093cea]
/usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so(+0x14371)[0x7f550409c371]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python[0x448edf]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x43074e]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x480c73]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python[0x448edf]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x43074e]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x480c73]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x735)[0x4bd325]
/usr/bin/python(PyEval_EvalFrameEx+0x7eb)[0x4b6a5b]
/usr/bin/python(PyEval_EvalFrameEx+0xb07)[0x4b6d77]
======= Memory map: ========
00400000-00633000 r-xp 00000000 08:07 179533                             /usr/bin/python2.7
00832000-00833000 r--p 00232000 08:07 179533                             /usr/bin/python2.7
00833000-0089c000 rw-p 00233000 08:07 179533                             /usr/bin/python2.7
0089c000-008ae000 rw-p 00000000 00:00 0 
00cd3000-03676000 rw-p 00000000 00:00 0                                  [heap]
7f54e6efc000-7f54e6f37000 r-xp 00000000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7f54e6f37000-7f54e7137000 ---p 0003b000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7f54e7137000-7f54e7138000 r--p 0003b000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7f54e7138000-7f54e713c000 rw-p 0003c000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7f54e713c000-7f54e743d000 rw-p 00000000 00:00 0 
7f54e7531000-7f54e753d000 r-xp 00000000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7f54e753d000-7f54e773c000 ---p 0000c000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7f54e773c000-7f54e773d000 r--p 0000b000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7f54e773d000-7f54e773e000 rw-p 0000c000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7f54e773e000-7f54e773f000 r-xp 00000000 08:07 261551                     /usr/lib/python2.7/dist-packages/gi/_gi_cairo.so
7f54e773f000-7f54e793f000 ---p 00001000 08:07 261551                     /usr/lib/python2.7/dist-packages/gi/_gi_cairo.so
7f54e793f000-7f54e7940000 r--p 00001000 08:07 261551                     /usr/lib/python2.7/dist-packages/gi/_gi_cairo.so
7f54e7940000-7f54e7941000 rw-p 00002000 08:07 261551                     /usr/lib/python2.7/dist-packages/gi/_gi_cairo.so
7f54e7941000-7f54e7981000 r-xp 00000000 08:07 180086                     /usr/lib/libibus-1.0.so.0.0.0
7f54e7981000-7f54e7b81000 ---p 00040000 08:07 180086                     /usr/lib/libibus-1.0.so.0.0.0
7f54e7b81000-7f54e7b82000 r--p 00040000 08:07 180086                     /usr/lib/libibus-1.0.so.0.0.0
7f54e7b82000-7f54e7b83000 rw-p 00041000 08:07 180086                     /usr/lib/libibus-1.0.so.0.0.0
7f54e7b83000-7f54e7b84000 rw-p 00000000 00:00 0 
7f54e7b84000-7f54e7b8a000 r-xp 00000000 08:07 236715                     /usr/lib/gtk-3.0/3.0.0/immodules/im-ibus.so
7f54e7b8a000-7f54e7d89000 ---p 00006000 08:07 236715                     /usr/lib/gtk-3.0/3.0.0/immodules/im-ibus.so
7f54e7d89000-7f54e7d8a000 r--p 00005000 08:07 236715                     /usr/lib/gtk-3.0/3.0.0/immodules/im-ibus.so
7f54e7d8a000-7f54e7d8b000 rw-p 00006000 08:07 236715                     /usr/lib/gtk-3.0/3.0.0/immodules/im-ibus.so
7f54e7d8b000-7f54e7d8e000 r-xp 00000000 08:07 179605                     /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f54e7d8e000-7f54e7f8d000 ---p 00003000 08:07 179605                     /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f54e7f8d000-7f54e7f8e000 r--p 00002000 08:07 179605                     /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f54e7f8e000-7f54e7f8f000 rw-p 00003000 08:07 179605                     /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f54e7f8f000-7f54e7f90000 ---p 00000000 00:00 0 
7f54e7f90000-7f54e8a91000 rw-p 00000000 00:00 0 
7f54e8a91000-7f54e8ac7000 r-xp 00000000 08:07 182775                     /usr/lib/libcroco-0.6.so.3.0.1
7f54e8ac7000-7f54e8cc6000 ---p 00036000 08:07 182775                     /usr/lib/libcroco-0.6.so.3.0.1
7f54e8cc6000-7f54e8cc7000 r--p 00035000 08:07 182775                     /usr/lib/libcroco-0.6.so.3.0.1
7f54e8cc7000-7f54e8cca000 rw-p 00036000 08:07 182775                     /usr/lib/libcroco-0.6.so.3.0.1
7f54e8cca000-7f54e8cfe000 r-xp 00000000 08:07 196259                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f54e8cfe000-7f54e8efe000 ---p 00034000 08:07 196259                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f54e8efe000-7f54e8eff000 r--p 00034000 08:07 196259                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f54e8eff000-7f54e8f00000 rw-p 00035000 08:07 196259                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f54e8f00000-7f54eb200000 rw-p 00000000 00:00 0 
7f54eb23d000-7f54eb23f000 r-xp 00000000 08:07 204396                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f54eb23f000-7f54eb43e000 ---p 00002000 08:07 204396                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f54eb43e000-7f54eb43f000 r--p 00001000 08:07 204396                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f54eb43f000-7f54eb440000 rw-p 00002000 08:07 204396                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f54eb440000-7f54ec000000 r--p 00000000 08:07 424325                     /usr/share/icons/hicolor/icon-theme.cache
7f54ec000000-7f54ec048000 rw-p 00000000 00:00 0 
7f54ec048000-7f54f0000000 ---p 00000000 00:00 0 
7f54f0173000-7f54f038b000 r--p 00000000 08:07 426230                     /usr/share/icons/gnome/icon-theme.cache
7f54f038b000-7f54f0474000 r--p 00000000 08:07 426226                     /usr/share/icons/Humanity/icon-theme.cache
7f54f0474000-7f54f0675000 rw-p 00000000 00:00 0 
7f54f0676000-7f54f0681000 r--p 00000000 08:07 426228                     /usr/share/icons/Humanity-Dark/icon-theme.cache
7f54f0681000-7f54f06a4000 r--p 00000000 08:07 426234                     /usr/share/icons/ubuntu-mono-dark/icon-theme.cache
7f54f06a4000-7f54f06f6000 r--p 00000000 08:07 337683                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
7f54f06f6000-7f54f0d17000 rw-p 00000000 00:00 0 
7f54f0d17000-7f54f0d18000 ---p 00000000 00:00 0 
7f54f0d18000-7f54f1518000 rw-p 00000000 00:00 0 
7f54f1518000-7f54f1519000 ---p 00000000 00:00 0 
7f54f1519000-7f54f1d19000 rw-p 00000000 00:00 0 
7f54f1d19000-7f54f1d1a000 ---p 00000000 00:00 0 
7f54f1d1a000-7f54f251a000 rw-p 00000000 00:00 0 
7f54f251a000-7f54f2531000 r-xp 00000000 08:07 792365                     /usr/lib/libdbusmenu-glib.so.4.0.5
7f54f2531000-7f54f2731000 ---p 00017000 08:07 792365                     /usr/lib/libdbusmenu-glib.so.4.0.5
7f54f2731000-7f54f2732000 r--p 00017000 08:07 792365                     /usr/lib/libdbusmenu-glib.so.4.0.5
7f54f2732000-7f54f2733000 rw-p 00018000 08:07 792365                     /usr/lib/libdbusmenu-glib.so.4.0.5
7f54f2733000-7f54f2744000 r-xp 00000000 08:07 792371                     /usr/lib/libdbusmenu-gtk3.so.4.0.5
7f54f2744000-7f54f2943000 ---p 00011000 08:07 792371                     /usr/lib/libdbusmenu-gtk3.so.4.0.5
7f54f2943000-7f54f2944000 r--p 00010000 08:07 792371                     /usr/lib/libdbusmenu-gtk3.so.4.0.5
7f54f2944000-7f54f2945000 rw-p 00011000 08:07 792371                     /usr/lib/libdbusmenu-gtk3.so.4.0.5
7f54f294c000-7f54f296a000 r--p 00000000 08:07 302453                     /usr/share/glib-2.0/schemas/gschemas.compiled
7f54f296a000-7f54f296f000 r-xp 00000000 08:07 329462                     /usr/lib/gtk-3.0/3.0.0/menuproxies/libappmenu.so
7f54f296f000-7f54f2b6e000 ---p 00005000 08:07 329462                     /usr/lib/gtk-3.0/3.0.0/menuproxies/libappmenu.so
7f54f2b6e000-7f54f2b6f000 r--p 00004000 08:07 329462                     /usr/lib/gtk-3.0/3.0.0/menuproxies/libappmenu.so
7f54f2b6f000-7f54f2b70000 rw-p 00005000 08:07 329462                     /usr/lib/gtk-3.0/3.0.0/menuproxies/libappmenu.so
7f54f2b70000-7f54f2b71000 ---p 00000000 00:00 0 
7f54f2b71000-7f54f3479000 rw-p 00000000 00:00 0 
7f54f3479000-7f54f347a000 ---p 00000000 00:00 0 
7f54f347a000-7f54f3c7a000 rw-p 00000000 00:00 0 
7f54f3c7a000-7f54f3c90000 r-xp 00000000 08:07 196009                     /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
7f54f3c90000-7f54f3e8f000 ---p 00016000 08:07 196009                     /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
7f54f3e8f000-7f54f3e90000 r--p 00015000 08:07 196009                     /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
7f54f3e90000-7f54f3e91000 rw-p 00016000 08:07 196009                     /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
7f54f3e91000-7f54f3e94000 rw-p 00000000 00:00 0 
7f54f3e94000-7f54f3e9b000 r-xp 00000000 08:07 1011851                    /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
7f54f3e9b000-7f54f409a000 ---p 00007000 08:07 1011851                    /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
7f54f409a000-7f54f409b000 r--p 00006000 08:07 1011851                    /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
7f54f409b000-7f54f409c000 rw-p 00007000 08:07 1011851                    /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
7f54f409c000-7f54f4edc000 r--p 00000000 08:07 183105                     /usr/lib/libicudata.so.44.2
7f54f4edc000-7f54f50db000 ---p 00e40000 08:07 183105                     /usr/lib/libicudata.so.44.2
7f54f50db000-7f54f50dc000 rw-p 00e3f000 08:07 183105                     /usr/lib/libicudata.so.44.2
7f54f50dc000-7f54f513b000 r-xp 00000000 08:07 1011853                    /usr/lib/x86_64-linux-gnu/libXt.so.6.0.0
7f54f513b000-7f54f533a000 ---p 0005f000 08:07 1011853                    /usr/lib/x86_64-linux-gnu/libXt.so.6.0.0
7f54f533a000-7f54f533b000 r--p 0005e000 08:07 1011853                    /usr/lib/x86_64-linux-gnu/libXt.so.6.0.0
7f54f533b000-7f54f5340000 rw-p 0005f000 08:07 1011853                    /usr/lib/x86_64-linux-gnu/libXt.so.6.0.0
7f54f5340000-7f54f5341000 rw-p 00000000 00:00 0 
7f54f5341000-7f54f5475000 r-xp 00000000 08:07 183119                     /usr/lib/libicuuc.so.44.2
7f54f5475000-7f54f5675000 ---p 00134000 08:07 183119                     /usr/lib/libicuuc.so.44.2
7f54f5675000-7f54f5684000 r--p 00134000 08:07 183119                     /usr/lib/libicuuc.so.44.2
7f54f5684000-7f54f5685000 rw-p 00143000 08:07 183119                     /usr/lib/libicuuc.so.44.2
7f54f5685000-7f54f5689000 rw-p 00000000 00:00 0 
7f54f5689000-7f54f583a000 r-xp 00000000 08:07 183107                     /usr/lib/libicui18n.so.44.2
7f54f583a000-7f54f5a3a000 ---p 001b1000 08:07 183107                     /usr/lib/libicui18n.so.44.2
7f54f5a3a000-7f54f5a45000 r--p 001b1000 08:07 183107                     /usr/lib/libicui18n.so.44.2
7f54f5a45000-7f54f5a46000 rw-p 001bc000 08:07 183107                     /usr/lib/libicui18n.so.44.2
7f54f5a46000-7f54f5a47000 rw-p 00000000 00:00 0 
7f54f5a47000-7f54f5ae2000 r-xp 00000000 08:07 196575                     /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f54f5ae2000-7f54f5ce1000 ---p 0009b000 08:07 196575                     /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f54f5ce1000-7f54f5ce3000 r--p 0009a000 08:07 196575                     /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f54f5ce3000-7f54f5ce5000 rw-p 0009c000 08:07 196575                     /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f54f5ce5000-7f54f5ce6000 rw-p 00000000 00:00 0 
7f54f5ce6000-7f54f5e37000 r-xp 00000000 08:07 791818                     /usr/lib/libxml2.so.2.7.8
7f54f5e37000-7f54f6036000 ---p 00151000 08:07 791818                     /usr/lib/libxml2.so.2.7.8
7f54f6036000-7f54f603e000 r--p 00150000 08:07 791818                     /usr/lib/libxml2.so.2.7.8
7f54f603e000-7f54f6040000 rw-p 00158000 08:07 791818                     /usr/lib/libxml2.so.2.7.8
7f54f6040000-7f54f6041000 rw-p 00000000 00:00 0 
7f54f6041000-7f54f607b000 r-xp 00000000 08:07 180499                     /usr/lib/libxslt.so.1.1.26
7f54f607b000-7f54f627a000 ---p 0003a000 08:07 180499                     /usr/lib/libxslt.so.1.1.26
7f54f627a000-7f54f627b000 r--p 00039000 08:07 180499                     /usr/lib/libxslt.so.1.1.26
7f54f627b000-7f54f627c000 rw-p 0003a000 08:07 180499                     /usr/lib/libxslt.so.1.1.26
7f54f627c000-7f54f62dc000 r-xp 00000000 08:07 792552                     /usr/lib/libsoup-2.4.so.1.4.0
7f54f62dc000-7f54f64dc000 ---p 00060000 08:07 792552                     /usr/lib/libsoup-2.4.so.1.4.0
7f54f64dc000-7f54f64de000 r--p 00060000 08:07 792552                     /usr/lib/libsoup-2.4.so.1.4.0
7f54f64de000-7f54f64e0000 rw-p 00062000 08:07 792552                     /usr/lib/libsoup-2.4.so.1.4.0
7f54f64e0000-7f54f6504000 r-xp 00000000 08:07 196022                     /usr/lib/x86_64-linux-gnu/libjpeg.so.62.0.0
7f54f6504000-7f54f6703000 ---p 00024000 08:07 196022                     /usr/lib/x86_64-linux-gnu/libjpeg.so.62.0.0
7f54f6703000-7f54f6704000 r--p 00023000 08:07 196022                     /usr/lib/x86_64-linux-gnu/libjpeg.so.62.0.0
7f54f6704000-7f54f6705000 rw-p 00024000 08:07 196022                     /usr/lib/x86_64-linux-gnu/libjpeg.so.62.0.0
7f54f6705000-7f54f67e2000 r-xp 00000000 08:07 791832                     /usr/lib/libgstreamer-0.10.so.0.29.0
7f54f67e2000-7f54f69e1000 ---p 000dd000 08:07 791832                     /usr/lib/libgstreamer-0.10.so.0.29.0
7f54f69e1000-7f54f69e6000 r--p 000dc000 08:07 791832                     /usr/lib/libgstreamer-0.10.so.0.29.0Aborted

---

### Post by jrizeks@gmail.com on 2011-10-18
I wonder if we reinstall the Software Center if it will fix the issue.  I have being using Ubuntu for 2 months so i am not sure if we are able to uninstall the Software Center and them install it back again.

---

### Post by mc4man on 2011-10-18
Run this 
```
gedit ~/.local/share/applications/mimeapps.list
```
In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

Or post the file, normally the above woouldn't affect 
S-c

---

### Post by jrizeks@gmail.com on 2011-10-18
ok, just one question when you tell me to run this command, do you want me to do this in the Terminal?

---

### Post by mc4man on 2011-10-18
Sorry - yes, run in a terminal

---

### Post by jrizeks@gmail.com on 2011-10-18
Wow, Thank you so much, it works great now..... Thank you again for your help.  Now even my Software Center is working. Like I say I am new to Ubuntu , i am a fast learner because i ask questions so i am going to bother you one more time and ask you what was the problem, was something being associate wrong in the setting?  Thank you again.

---

### Post by mc4man on 2011-10-18
The issue is caused by the default section's line for opening directories is specifying a .desktop that no longer is used
nautilus itself ignores this but several other action don't
So when the default couldn't be found generally then the 1st listed in the added associations sections is used

Not sure if that's exactly what happened to you - would be unusual to have Sc listed in an inode/directory= line in the Added section

This is why you see a number of posts about vlc, banshee  ect being opened

A bit more of a descript on the bug I filed against this (the bug will probably languish
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

Actually i'd probably just delete the mimeapps.list file entirely & start fresh - though if you had some associations in there to custom commands you wanted to keep then leave (userapp.desktops

If you'd like post your mimeapps.list in a code box, we could take a look

---

### Post by elephantgod on 2012-02-23
> **mc4man said:**
> Run this 
```
gedit ~/.local/share/applications/mimeapps.list
```
In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

Or post the file, normally the above woouldn't affect 
S-c

Hi

i met the exact same problem here. But in my **mimeapps.list** , there is no **inode/directory=**, here is mine:
```

[Added Associations]
application/x-compressed-tar=ubuntu-software-center.desktop;
x-scheme-handler/http=google-chrome.desktop;
x-scheme-handler/https=google-chrome.desktop;
text/x-install=emacs.desktop;

[Default Applications]
application/x-compressed-tar=file-roller.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
text/x-install=emacs.desktop
```

how can i fix my problem?

Thank!

---

