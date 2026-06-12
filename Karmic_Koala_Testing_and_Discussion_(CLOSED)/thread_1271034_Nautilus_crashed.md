---
title: "Nautilus crashed"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Szise on 2009-09-20
When i type "sudo nautilus" i'm receiving this error:

> 
Sense key: 0x70 0x00 0x02 0.....

Segmentation fault (core dumped)

> 
*** glibc detected *** nautilus: double free or corruption (fasttop): 0x0a2850b0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x917fff1]
/lib/tls/i686/cmov/libc.so.6[0x91816f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x918479d]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0x4c4266]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x330)[0xe1b8e0]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x2c2)[0xe1c502]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x6e)[0xe1c67e]
/usr/lib/libgstreamer-0.10.so.0[0x146dedf]
/usr/lib/libgstreamer-0.10.so.0(gst_registry_binary_read_cache+0x3e5)[0x146f6f5]
/usr/lib/libgstreamer-0.10.so.0[0x13fb5d5]
/usr/lib/libgstreamer-0.10.so.0[0x13fce65]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x440)[0x4cac10]
/usr/lib/libgstreamer-0.10.so.0(gst_init_check+0xee)[0x13fc4ae]
/usr/lib/libbrasero-burn.so.0(brasero_burn_library_start+0x6e)[0x85f7a5e]
/usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so(nautilus_module_initialize+0x2f)[0x6ed62ef]
nautilus[0x8145ede]
/usr/lib/libgobject-2.0.so.0(g_type_module_use+0x90)[0xe388c0]
nautilus[0x814601a]
nautilus[0x806f9bf]
nautilus[0x80814c8]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x912bb56]
nautilus[0x806bf41]
======= Memory map: ========
00110000-00117000 r-xp 00000000 08:07 23789      /usr/lib/libXrandr.so.2.2.0
00117000-00118000 r--p 00006000 08:07 23789      /usr/lib/libXrandr.so.2.2.0
00118000-00119000 rw-p 00007000 08:07 23789      /usr/lib/libXrandr.so.2.2.0
00119000-00120000 r-xp 00000000 08:07 4200       /lib/tls/i686/cmov/librt-2.10.1.so
00120000-00121000 r--p 00006000 08:07 4200       /lib/tls/i686/cmov/librt-2.10.1.so
00121000-00122000 rw-p 00007000 08:07 4200       /lib/tls/i686/cmov/librt-2.10.1.so
00123000-00149000 r-xp 00000000 08:07 24708      /usr/lib/libgnome-desktop-2.so.11.4.1
00149000-0014a000 r--p 00025000 08:07 24708      /usr/lib/libgnome-desktop-2.so.11.4.1
0014a000-0014b000 rw-p 00026000 08:07 24708      /usr/lib/libgnome-desktop-2.so.11.4.1
0014b000-001f8000 r-xp 00000000 08:07 4301       /usr/lib/libgio-2.0.so.0.2106.0
001f8000-001f9000 ---p 000ad000 08:07 4301       /usr/lib/libgio-2.0.so.0.2106.0
001f9000-001fa000 r--p 000ad000 08:07 4301       /usr/lib/libgio-2.0.so.0.2106.0
001fa000-001fb000 rw-p 000ae000 08:07 4301       /usr/lib/libgio-2.0.so.0.2106.0
001fb000-001fc000 rw-p 00000000 00:00 0 
001fc000-00242000 r-xp 00000000 08:07 23707      /usr/lib/libpango-1.0.so.0.2506.0
00242000-00243000 r--p 00046000 08:07 23707      /usr/lib/libpango-1.0.so.0.2506.0
00243000-00244000 rw-p 00047000 08:07 23707      /usr/lib/libpango-1.0.so.0.2506.0
00244000-00246000 r-xp 00000000 08:07 23745      /usr/lib/libXcomposite.so.1.0.0
00246000-00247000 r--p 00001000 08:07 23745      /usr/lib/libXcomposite.so.1.0.0
00247000-00248000 rw-p 00002000 08:07 23745      /usr/lib/libXcomposite.so.1.0.0
00248000-0024a000 r-xp 00000000 08:07 23766      /usr/lib/libXdamage.so.1.1.0
0024a000-0024b000 rw-p 00001000 08:07 23766      /usr/lib/libXdamage.so.1.1.0
0024b000-0024d000 r-xp 00000000 08:07 23777      /usr/lib/libXinerama.so.1.0.0
0024d000-0024e000 rw-p 00001000 08:07 23777      /usr/lib/libXinerama.so.1.0.0
0024f000-002fb000 r-xp 00000000 08:07 23847      /usr/lib/libgdk-x11-2.0.so.0.1711.0
002fb000-002fd000 r--p 000ab000 08:07 23847      /usr/lib/libgdk-x11-2.0.so.0.1711.0
002fd000-002fe000 rw-p 000ad000 08:07 23847      /usr/lib/libgdk-x11-2.0.so.0.1711.0
002fe000-00382000 r-xp 00000000 08:07 23527      /usr/lib/libcairo.so.2.10800.8
00382000-00384000 r--p 00083000 08:07 23527      /usr/lib/libcairo.so.2.10800.8
00384000-00385000 rw-p 00085000 08:07 23527      /usr/lib/libcairo.so.2.10800.8
00385000-003a1000 r-xp 00000000 08:07 1013       /lib/libselinux.so.1
003a1000-003a2000 r--p 0001b000 08:07 1013       /lib/libselinux.so.1
003a2000-003a3000 rw-p 0001c000 08:07 1013       /lib/libselinux.so.1
003a3000-003cb000 r-xp 00000000 08:07 23709      /usr/lib/libpangoft2-1.0.so.0.2506.0
003cb000-003cc000 r--p 00027000 08:07 23709      /usr/lib/libpangoft2-1.0.so.0.2506.0
003cc000-003cd000 rw-p 00028000 08:07 23709      /usr/lib/libpangoft2-1.0.so.0.2506.0
003cd000-003d8000 r-xp 00000000 08:07 23708      /usr/lib/libpangocairo-1.0.so.0.2506.0
003d8000-003d9000 r--p 0000a000 08:07 23708      /usr/lib/libpangocairo-1.0.so.0.2506.0
003d9000-003da000 rw-p 0000b000 08:07 23708      /usr/lib/libpangocairo-1.0.so.0.2506.0
003da000-003de000 r-xp 00000000 08:07 15677      /usr/lib/libXfixes.so.3.1.0
003de000-003df000 r--p 00003000 08:07 15677      /usr/lib/libXfixes.so.3.1.0
003df000-003e0000 rw-p 00004000 08:07 15677      /usr/lib/libXfixes.so.3.1.0
003e0000-003e2000 r-xp 00000000 08:07 4187       /lib/tls/i686/cmov/libdl-2.10.1.so
003e2000-003e3000 r--p 00002000 08:07 4187       /lib/tls/i686/cmov/libdl-2.10.1.so
003e3000-003e4000 rw-p 00003000 08:07 4187       /lib/tls/i686/cmov/libdl-2.10.1.so
003e6000-003e9000 r-xp 00000000 08:07 24795      /usr/lib/liblaunchpad-integration.so.1.0.0
003e9000-003ea000 r--p 00002000 08:07 24795      /usr/lib/liblaunchpad-integration.so.1.0.0
003ea000-003eb000 rw-p 00003000 08:07 24795      /usr/lib/liblaunchpad-integration.so.1.0.0
003eb000-003ff000 r-xp 00000000 08:07 3088       /lib/libz.so.1.2.3.3
003ff000-00400000 r--p 00013000 08:07 3088       /lib/libz.so.1.2.3.3
00400000-00401000 rw-p 00014000 08:07 3088       /lib/libz.so.1.2.3.3
00401000-0042c000 r-xp 00000000 08:07 17963      /usr/lib/libfontconfig.so.1.3.0
0042c000-0042d000 r--p 0002a000 08:07 17963      /usr/lib/libfontconfig.so.1.3.0
0042d000-0042e000 rw-p 0002b000 08:07 17963      /usr/lib/libfontconfig.so.1.3.0
0042e000-0043c000 r-xp 00000000 08:07 15721      /usr/lib/libXext.so.6.4.0
0043c000-0043d000 r--p 0000d000 08:07 15721      /usr/lib/libXext.so.6.4.0
0043d000-0043e000 rw-p 0000e000 08:07 15721      /usr/lib/libXext.so.6.4.0
0043e000-00441000 r-xp 00000000 08:07 23508      /usr/lib/libxcb-render-util.so.0.0.0
00441000-00442000 r--p 00002000 08:07 23508      /usr/lib/libxcb-render-util.so.0.0.0
00442000-00443000 rw-p 00003000 08:07 23508      /usr/lib/libxcb-render-util.so.0.0.0
00445000-0044c000 r-xp 00000000 08:07 24586      /usr/lib/libgailutil.so.18.0.1
0044c000-0044d000 r--p 00006000 08:07 24586      /usr/lib/libgailutil.so.18.0.1
0044d000-0044e000 rw-p 00007000 08:07 24586      /usr/lib/libgailutil.so.18.0.1
0044e000-00457000 r-xp 00000000 08:07 23755      /usr/lib/libXcursor.so.1.0.2
00457000-00458000 r--p 00008000 08:07 23755      /usr/lib/libXcursor.so.1.0.2
00458000-00459000 rw-p 00009000 08:07 23755      /usr/lib/libXcursor.so.1.0.2
00459000-0046b000 r-xp 00000000 08:07 4199       /lib/tls/i686/cmov/libresolv-2.10.1.so
0046b000-0046c000 r--p 00011000 08:07 4199       /lib/tls/i686/cmov/libresolv-2.10.1.so
0046c000-0046d000 rw-p 00012000 08:07 4199       /lib/tls/i686/cmov/libresolv-2.10.1.so
0046d000-0046f000 rw-p 00000000 00:00 0 
0046f000-00477000 r-xp 00000000 08:07 23427      /usr/lib/libfusion-1.2.so.0.7.0
00477000-00478000 r--p 00007000 08:07 23427      /usr/lib/libfusion-1.2.so.0.7.0
00478000-00479000 rw-p 00008000 08:07 23427      /usr/lib/libfusion-1.2.so.0.7.0
00479000-0047b000 r-xp 00000000 08:07 24683      /usr/lib/libxcb-event.so.1.0.0
0047b000-0047c000 r--p 00001000 08:07 24683      /usr/lib/libxcb-event.so.1.0.0Aborted (core dumped)


---

### Post by ajgreeny on 2009-09-20
It may not make any difference but try ```
gksudo nautilus
```
You should always use gksudo (gnome) or kdesu (kde) for applications with a gui.  sudo is for cli applications and utilities only.

---

### Post by ubername on 2009-09-20
gksu dbus-launch nautilus

seems to work for me. There are other threads on this topic.

---

### Post by handaxe on 2009-09-20
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/420841](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/420841)

HA

---

### Post by handaxe on 2009-09-22
```
gksudo nautilus
``` now works as it should in nautilus 2.28, at least for me and according to the devs

HA

---

