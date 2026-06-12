---
title: "Serious 7.10 Problems"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Slayta on 2007-10-26
I'm not very good with this stuff. but after i installed 7.10 everything is crashing. I tried running a few things with the console and this is what happened. 

[SIZE="1"]**root@mike-laptop:/home/mike# update-manager **
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
**root@mike-laptop:/home/mike# synaptic **
*** glibc detected *** synaptic: munmap_chunk(): invalid pointer: 0x088f6540 ***
======= Backtrace: =========
/lib/libc.so.6[0xb72fa0f7]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7646961]
/usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so[0xb6fcfe96]
/usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so[0xb6fcb843]
/usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so[0xb6fcd1c3]
/usr/lib/libgtk-x11-2.0.so.0(gtk_paint_box+0xaa)[0xb7ccefea]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_button_paint+0x29a)[0xb7b7f78a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b7f88e]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c591de]
/usr/lib/libgobject-2.0.so.0[0xb76ddf89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20c)[0xb76df85c]
/usr/lib/libgobject-2.0.so.0[0xb76f0973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb76f160f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb76f1a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d77498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x139)[0xb7bbb099]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbb131]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b7a2b1]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb7bbbb2b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbbbf4]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c591de]
/usr/lib/libgobject-2.0.so.0[0xb76ddf89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20c)[0xb76df85c]
/usr/lib/libgobject-2.0.so.0[0xb76f0973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb76f160f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb76f1a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d77498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x139)[0xb7bbb099]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbb131]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b7a2b1]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb7bbbb2b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbbbf4]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c591de]
/usr/lib/libgobject-2.0.so.0[0xb76ddf89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20c)[0xb76df85c]
/usr/lib/libgobject-2.0.so.0[0xb76f0973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb76f160f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb76f1a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d77498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x139)[0xb7bbb099]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbb131]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b763df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb7bbbb2b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbbbf4]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d8ead1]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c591de]
/usr/lib/libgobject-2.0.so.0[0xb76ddf89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb76df772]
/usr/lib/libgobject-2.0.so.0[0xb76f0973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb76f160f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb76f1a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d77498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x507)[0xb7c53787]
/usr/lib/libgdk-x11-2.0.so.0[0xb798b06f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb798b73a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bbbd8f]
/usr/lib/libgdk-x11-2.0.so.0[0xb79715e8]
/usr/lib/libglib-2.0.so.0[0xb763d551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb763f11c]
/usr/lib/libglib-2.0.so.0[0xb764255f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7642909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_dialog_run+0x18b)[0xb7bcd77b]
synaptic[0x8098b32]
======= Memory map: ========
08048000-080ff000 r-xp 00000000 08:01 5015756    /usr/sbin/synaptic
080ff000-08102000 rw-p 000b7000 08:01 5015756    /usr/sbin/synaptic
08102000-0899c000 rw-p 08102000 00:00 0          [heap]
b4626000-b4775000 rw-p b4626000 00:00 0 
b4775000-b5211000 r--s 00000000 08:01 4997217    /var/cache/apt/pkgcache.bin
b5211000-b5271000 rw-s 00000000 00:08 819213     /SYSV00000000 (deleted)
b5271000-b52f5000 r--p 00000000 08:01 5473631    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b52f5000-b52fb000 r-xp 00000000 08:01 6457456    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b52fb000-b52fc000 rw-p 00005000 08:01 6457456    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b52fc000-b52fe000 r-xp 00000000 08:01 5145262    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b52fe000-b52ff000 rw-p 00001000 08:01 5145262    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b52ff000-b538a000 r--p 00000000 08:01 5473630    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b538a000-b5390000 r--s 00000000 08:01 4997551    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5390000-b5391000 r--s 00000000 08:01 5001843    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b5391000-b5394000 r--s 00000000 08:01 5001841    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5394000-b5395000 r--s 00000000 08:01 5001837    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5395000-b5396000 r--s 00000000 08:01 5001835    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5396000-b539a000 r--s 00000000 08:01 4999333    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b539a000-b539b000 r--s 00000000 08:01 5001833    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b539b000-b539d000 r--s 00000000 08:01 5001832    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b539d000-b539f000 r--s 00000000 08:01 5001813    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b539f000-b53a0000 r--s 00000000 08:01 5001800    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b53a0000-b53a2000 r--s 00000000 08:01 5001799    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b53a2000-b53a8000 r--s 00000000 08:01 4997540    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b53a8000-b53aa000 r--s 00000000 08:01 5001797    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b53aa000-b53ac000 r--s 00000000 08:01 5001785    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b53ac000-b53b4000 r--s 00000000 08:01 5001775    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b53b4000-b53ba000 r--s 00000000 08:01 5001774    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b53ba000-b53bb000 r--s 00000000 08:01 5001773    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b53bb000-b53bd000 r--s 00000000 08:01 5001728    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b53bd000-b53c3000 r--s 00000000 08:01 4997523    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b53c3000-b53c6000 r--s 00000000 08:01 5001582    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b53c6000-b53ca000 r--s 00000000 08:01 4997228    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b53ca000-b53cc000 r--s 00000000 08:01 4998964    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b53cc000-b53d0000 r-xp 00000000 08:01 5079540    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b53d0000-b53d1000 rw-p 00003000 08:01 5079540    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b53d2000-b53d8000 r--p 00000000 08:01 5259623    /usr/share/pixmaps/hicolor/icon-theme.cache
b53d8000-b64c1000 r--p 00000000 08:01 5443847    /usr/share/icons/crystalsvg/icon-theme.cache
b64c1000-b6b68000 r--p 00000000 08:01 5357955    /usr/share/icons/gnome/icon-theme.cache
b6b68000-b6dbf000 r--p 00000000 08:01 5362004    /usr/share/icons/Tango/icon-theme.cache
b6dbf000-b6e60000 r--p 00000000 08:01 5362002    /usr/share/icons/Tangerine/icon-theme.cache
b6e60000-b6fc6000 r--p 00000000 08:01 5361702    /usr/share/icons/Human/icon-theme.cache
b6fc6000-b6fd1000 r-xp 00000000 08:01 5079059    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b6fd1000-b6fd2000 rw-p 0000b000 08:01 5079059    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b6fd2000-b6ff2000 r--p 00000000 08:01 5456133    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
b6ff2000-b6ffa000 r-xp 00000000 08:01 1966430    /lib/libnss_files-2.6.1.so
b6ffa000-b6ffc000 rw-p 00007000 08:01 1966430    /lib/libnss_files-2.6.1.so
b6ffc000-b7004000 r-xp 00000000 08:01 1966432    /lib/libnss_nis-2.6.1.so
b7004000-b7006000 rw-p 00007000 08:01 1966432    /lib/libnss_nis-2.6.1.so
b7006000-b7019000 r-xp 00000000 08:01 1966427    /lib/libnsl-2.6.1.so
b7019000-b701b000 rw-p 00012000 08:01 1966427    /lib/libnsl-2.6.1.so
b701b000-b701d000 rw-p b701b000 00:00 0 
b701d000-b7023000 r-xp 00000000 08:01 1966428    /lib/libnss_compat-2.6.1.so
b7023000-b7025000 rw-p 00005000 08:01 1966428    /lib/libnss_compat-2.6.1.so
b7025000-b7026000 r--p 00000000 08:01 5456140    /usr/share/locale-langpack/en_CA/LC_MESSAGES/launchpad-integration.mo
b7026000-b7028000 r--s 00000000 08:01 4999345    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7028000-b702a000 r--p 00000000 08:01 5456055    /usr/share/locale-langpack/en_CA/LC_MESSAGES/atk10.mo
b702a000-b702f000 r--p 00000000 08:01 5456095    /usr/share/locale-langpack/en_CA/LC_MESSAGES/glib20.mo
b702f000-b7030000 r--p 00000000 08:01 5456173    /usr/share/locale-langpack/en_CA/LC_MESSAGES/synaptic.mo
b7030000-b7031000 r-xp 00000000 08:01 9289907    /usr/lib/gconv/ISO8859-1.so
b7031000-b7033000 rw-p 00000000 08:01 9289907    /usr/lib/gconv/ISO8859-1.so
b7033000-b7042000 r--p 00000000 08:01 5456134    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20.mo
b7042000-b707d000 r--p 00000000 08:01 5079944    /usr/lib/locale/en_CA.utf8/LC_CTYPE
b707d000-b707e000 r--p 00000000 08:01 5079949    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
b707e000-b707f000 r--p 00000000 08:01 5079952    /usr/lib/locale/en_CA.utf8/LC_TIME
b707f000-b7156000 r--p 00000000 08:01 5079943    /usr/lib/locale/en_CA.utf8/LC_COLLATE
b7156000-b7157000 r--p 00000000 08:01 5079947    /usr/lib/locale/en_CA.utf8/LC_MONETARY
b7157000-b715a000 rw-p b7157000 00:00 0 
b715a000-b7196000 r-xp 00000000 08:01 1966199    /lib/libncurses.so.5.6
b7196000-b719e000 rw-p 0003b000 08:01 1966199    /lib/libncurses.so.5.6
b719e000-b71b3000 r-xp 00000000 08:01 5016183    /usr/lib/libICE.so.6.3.0
b71b3000-b71b5000 rw-p 00014000 08:01 5016183    /usr/lib/libICE.so.6.3.0
b71b5000-b71b6000 rw-p b71b5000 00:00 0 
b71b6000-b71bd000 r-xp 00000000 08:01 5015000    /usr/lib/libSM.so.6.0.0
b71bd000-b71be000 rw-p 00006000 08:01 5015000    /usr/lib/libSM.so.6.0.0
b71be000-b71c2000 r-xp 00000000 08:01 5013713    /usr/lib/libXdmcp.so.6.0.0
b71c2000-b71c3000 rw-p 00003000 08:01 5013713    /usr/lib/libXdmcp.so.6.0.0
b71c3000-b71e5000 r-xp 00000000 08:01 5013705    /usr/lib/libpng12.so.0.15.0
b71e5000-b71e6000 rw-p 00021000 08:01 5013705    /usr/lib/libpng12.so.0.15.0
b71e6000-b71e7000 rw-p b71e6000 00:00 0 
b71e7000-b71e9000 r-xp 00000000 08:01 5013527    /usr/lib/libXau.so.6.0.0
b71e9000-b71ea000 rw-p 00001000 08:01 5013527    /usr/lib/libXau.so.6.0.0
b71ea000-b7208000 r-xp 00000000 08:01 6013195    /usr/lib/libexpat.so.1.0.0
b7208000-b720a000 rw-p 0001e000 08:01 6013195    /usr/lib/libexpat.so.1.0.0
b720a000-b7276000 r-xp 00000000 08:01 5014088    /usr/lib/libfreetype.so.6.3.16
b7276000-b727a000 rw-p 0006b000 08:01 5014088    /usr/lib/libfreetype.so.6.3.16
b727a000-b728e000 r-xp 00000000 08:01 5013876    /usr/lib/libz.so.1.2.3.3
b728e000-b728f000 rw-p 00013000 08:01 5013876    /usr/lib/libz.so.1.2.3.3
b728f000-b7290000 rw-p b728f000 00:00 0 
b7290000-b7292000 r-xp 00000000 08:01 1966440    /lib/libutil-2.6.1.so
b7292000-b7294000 rw-p 00001000 08:01 1966440    /lib/libutil-2.6.1.so
b7294000-b73c2000 r-xp 00000000 08:01 1966419    /lib/libc-2.6.1.so
b73c2000-b73c3000 r--p 0012d000 08:01 1966419    /lib/libc-2.6.1.so
b73c3000-b73c5000 rw-p 0012e000 08:01 1966419    /lib/libc-2.6.1.so
b73c5000-b73c8000 rw-p b73c5000 00:00 0 
b73c8000-b73d2000 r-xp 00000000 08:01 1966211    /lib/libgcc_s.so.1
b73d2000-b73d3000 rw-p 0000a000 08:01 1966211    /lib/libgcc_s.so.1
b73d3000-b74bb000 r-xp 00000000 08:01 5014602    /usr/lib/libstdc++.so.6.0.9
b74bb000-b74be000 r--p 000e8000 08:01 5014602    /usr/lib/libstdc++.so.6.0.9
b74be000-b74c0000 rw-p 000eb000 08:01 5014602    /usr/lib/libstdc++.so.6.0.9
b74c0000-b74c6000 rw-p b74c0000 00:00 0 
b74c6000-b74d9000 r-xp 00000000 08:01 1966435    /lib/libpthread-2.6.1.so
b74d9000-b74db000 rw-p 00012000 08:01 1966435    /lib/libpthread-2.6.1.so
b74db000-b74dd000 rw-p b74db000 00:00 0 
b74dd000-b74e0000 r-xp 00000000 08:01 5013557    /usr/lib/liblaunchpad-integration.so.0.0.0
b74e0000-b74e1000 rw-p 00002000 08:01 5013557    /usr/lib/liblaunchpad-integration.so.0.0.0
b74e1000-b74e2000 rw-p b74e1000 00:00 0 
b74e2000-b750f000 r-xp 00000000 08:01 5015045    /usr/lib/libpangoft2-1.0.so.0.1800.2
b750f000-b7510000 rw-p 0002c000 08:01 5015045    /usr/lib/libpangoft2-1.0.so.0.1800.2
b7510000-b7533000 r-xp 00000000 08:01 1966425    /lib/libm-2.6.1.so
b7533000-b7535000 rw-p 00022000 08:01 1966425    /lib/libm-2.6.1.so
b7535000-b753f000 r-xp 00000000 08:01 5015049    /usr/lib/libpangox-1.0.so.0.1800.2
b753f000-b7540000 rw-p 0000a000 08:01 5015049    /usr/lib/libpangox-1.0.so.0.1800.2
b7540000-b7546000 r-xp 00000000 08:01 5015065    /usr/lib/libpangoxft-1.0.so.0.1800.2
b7546000-b7547000 rw-p 00005000 08:01 5015065    /usr/lib/libpangoxft-1.0.so.0.1800.2
b7547000-b7558000 r-xp 00000000 08:01 5013781    /usr/lib/libXft.so.2.1.2
b7558000-b7559000 rw-p 00010000 08:01 5013781    /usr/lib/libXft.so.2.1.2
b7559000-b760b000 r-xp 00000000 08:01 5015323    /usr/lib/libvte.so.9.2.13
b760b000-b760f000 rw-p 000b1000 08:01 5015323    /usr/lib/libvte.so.9.2.13
b760f000-b7610000 rw-p b760f000 00:00 0 
b7610000-b76cc000 r-xp 00000000 08:01 5014431    /usr/lib/libglib-2.0.so.0.1400.1
b76cc000-b76cd000 rw-p 000bc000 08:01 5014431    /usr/lib/libglib-2.0.so.0.1400.1
b76cd000-b76cf000 r-xp 00000000 08:01 1966423    /lib/libdl-2.6.1.so
b76cf000-b76d1000 rw-p 00001000 08:01 1966423    /lib/libdl-2.6.1.so
b76d1000-b76d4000 r-xp 00000000 08:01 5014446    /usr/lib/libgmodule-2.0.so.0.1400.1
b76d4000-b76d5000 rw-p 00002000 08:01 5014446    /usr/lib/libgmodule-2.0.so.0.1400.1
b76d5000-b770f000 r-xp 00000000 08:01 5014447    /usr/lib/libgobject-2.0.so.0.1400.1
b770f000-b7710000 rw-p 0003a000 08:01 5014447    /usr/lib/libgobject-2.0.so.0.1400.1
b7710000-b774b000 r-xp 00000000 08:01 5015039    /usr/lib/libpango-1.0.so.0.1800.2
b774b000-b774d000 rw-p 0003b000 08:01 5015039    /usr/lib/libpango-1.0.so.0.1800.2
b774d000-b7751000 r-xp 00000000 08:01 5014545    /usr/lib/libXfixes.so.3.1.0
b7751000-b7752000 rw-p 00003000 08:01 5014545    /usr/lib/libXfixes.so.3.1.0
b7752000-b7753000 rw-p b7752000 00:00 0 
b7753000-b7840000 r-xp 00000000 08:01 5014327    /usr/lib/libX11.so.6.2.0
b7840000-b7844000 rw-p 000ed000 08:01 5014327    /usr/lib/libX11.so.6.2.0
b7844000-b78b9000 r-xp 00000000 08:01 5014395    /usr/lib/libcairo.so.2.11.5
b78b9000-b78bb000 rw-p 00074000 08:01 5014395    /usr/lib/libcairo.so.2.11.5
b78bb000-b78bd000 r-xp 00000000 08:01 5014555    /usr/lib/libXdamage.so.1.1.0
b78bd000-b78be000 rw-p 00001000 08:01 5014555    /usr/lib/libXdamage.so.1.1.0
b78be000-b78c0000 r-xp 00000000 08:01 5015235    /usr/lib/libXcomposite.so.1.0.0
b78c0000-b78c1000 rw-p 00001000 08:01 5015235    /usr/lib/libXcomposite.so.1.0.0
b78c1000-b78c9000 r-xp 00000000 08:01 5015033    /usr/lib/libXcursor.so.1.0.2
b78c9000-b78ca000 rw-p 00007000 08:01 5015033    /usr/lib/libXcursor.so.1.0.2
b78ca000-b78cf000 r-xp 00000000 08:01 5015053    /usr/lib/libXrandr.so.2.1.0
b78cf000-b78d0000 rw-p 00005000 08:01 5015053    /usr/lib/libXrandr.so.2.1.0
b78d0000-b78d1000 rw-p b78d0000 00:00 0 
b78d1000-b78d8000 r-xp 00000000 08:01 5015035    /usr/lib/libXi.so.6.0.0
b78d8000-b78d9000 rw-p 00006000 08:01 5015035    /usr/lib/libXi.so.6.0.0
b78d9000-b78db000 r-xp 00000000 08:01 5015051    /usr/lib/libXinerama.so.1.0.0
b78db000-b78dc000 rw-p 00001000 08:01 5015051    /usr/lib/libXinerama.so.1.0.0
b78dc000-b78e3000 r-xp 00000000 08:01 5014347    /usr/lib/libXrender.so.1.3.0
b78e3000-b78e4000 rw-p 00006000 08:01 5014347    /usr/lib/libXrender.so.1.3.0
b78e4000-b78f1000 r-xp 00000000 08:01 5014571    /usr/lib/libXext.so.6.4.0
b78f1000-b78f2000 rw-p 0000d000 08:01 5014571    /usr/lib/libXext.so.6.4.0
b78f2000-b7915000 r-xp 00000000 08:01 5013702    /usr/lib/libfontconfig.so.1.2.0
b7915000-b791d000 rw-p 00023000 08:01 5013702    /usr/lib/libfontconfig.so.1.2.0
b791d000-b7925000 r-xp 00000000 08:01 5015043    /usr/lib/libpangocairo-1.0.so.0.1800.2
b7925000-b7926000 rw-p 00007000 08:01 5015043    /usr/lib/libpangocairo-1.0.so.0.1800.2
b7926000-b7927000 rw-p b7926000 00:00 0 
b7927000-b793e000 r-xp 00000000 08:01 5016138    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b793e000-b793f000 rw-p 00016000 08:01 5016138    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b793f000-b7958000 r-xp 00000000 08:01 6013203    /usr/lib/libatk-1.0.so.0.2009.1
b7958000-b795a000 rw-p 00018000 08:01 6013203    /usr/lib/libatk-1.0.so.0.2009.1
b795a000-b79de000 r-xp 00000000 08:01 5015731    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79de000-b79e1000 rw-p 00084000 08:01 5015731    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79e1000-b7af9000 r-xp 00000000 08:01 5015292    /usr/lib/libxml2.so.2.6.30
b7af9000-b7afe000 rw-p 00118000 08:01 5015292    /usr/lib/libxml2.so.2.6.30
b7afe000-b7aff000 rw-p b7afe000 00:00 0 
b7aff000-b7e7c000 r-xp 00000000 08:01 5016373    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7e7c000-b7e83000 rw-p 0037c000 08:01 5016373    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7e83000-b7e84000 rw-p b7e83000 00:00 0 
b7e84000-b7e9b000 r-xp 00000000 08:01 5014349    /usr/lib/libglade-2.0.so.0.0.7
b7e9b000-b7e9c000 rw-p 00016000 08:01 5014349    /usr/lib/libglade-2.0.so.0.0.7
b7e9c000-b7e9d000 rw-p b7e9c000 00:00 0 
b7e9d000-b7eaf000 r-xp 00000000 08:01 5016357    /usr/lib/libapt-inst-libc6.6-6.so.1.1.0
b7eaf000-b7eb0000 rw-p 00011000 08:01 5016357    /usr/lib/libapt-inst-libc6.6-6.so.1.1.0
b7eb0000-b7f7c000 r-xp 00000000 08:01 5017498    /usr/lib/libapt-pkg-libc6.6-6.so.4.5.0
b7f7c000-b7f7f000 rw-p 000cb000 08:01 5017498    /usr/lib/libapt-pkg-libc6.6-6.so.4.5.0
b7f7f000-b7f80000 r--p 00000000 08:01 5079953    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f80000-b7f81000 r--p 00000000 08:01 5079950    /usr/lib/locale/en_CA.utf8/LC_PAPER
b7f81000-b7f82000 r--p 00000000 08:01 5079948    /usr/lib/locale/en_CA.utf8/LC_NAME
b7f82000-b7f83000 r--p 00000000 08:01 5079942    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
b7f83000-b7f84000 r--p 00000000 08:01 5079951    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
b7f84000-b7f85000 r--p 00000000 08:01 5079946    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
b7f85000-b7f8c000 r--s 00000000 08:01 5013626    /usr/lib/gconv/gconv-modules.cache
b7f8c000-b7f8d000 r--p 00000000 08:01 5079945    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
b7f8d000-b7f8e000 rw-p b7f8d000 00:00 0 
b7f8e000-b7fa8000 r-xp 00000000 08:01 1966416    /lib/ld-2.6.1.so
b7fa8000-b7faa000 rw-p 00019000 08:01 1966416    /lib/ld-2.6.1.so
bfe71000-bfe86000 rw-p bfe71000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
root@mike-laptop:/home/mike# 
[/SIZE]

---

### Post by thelocust on 2007-10-26
[SIZE=2]looks like you have to install some gtk python thing see if pygtk is in the repos.[/SIZE]

---

