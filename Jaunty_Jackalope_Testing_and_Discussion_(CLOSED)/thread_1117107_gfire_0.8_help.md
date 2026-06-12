---
title: "gfire 0.8 help"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by linux_lover69 on 2009-04-05
I installed gfire 0.8 on ubuntu jaunty and after setting up my xfire account in pidgin, pidgin would crash giving me this error. 
```
xp@xp-desktop:~$ pidgin
*** stack smashing detected ***: pidgin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7600da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7600d60]
/usr/lib/purple-2/libxfire.so[0xb5e62064]
/usr/lib/purple-2/libxfire.so(gfire_packet_131+0x579)[0xb5e5a09b]
/usr/lib/purple-2/libxfire.so(gfire_parse_packet+0x2ce)[0xb5e580a8]
/usr/lib/purple-2/libxfire.so(gfire_input_cb+0x47f)[0xb5e57dd2]
pidgin[0x80a8e93]
/usr/lib/libglib-2.0.so.0[0xb77cdc4d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7796a58]
/usr/lib/libglib-2.0.so.0[0xb7799fbb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb779a48a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7a885c9]
pidgin(main+0x89a)[0x80c31ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7519775]
pidgin[0x806db61]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 08:01 25723      /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 08:01 25723      /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 08:01 25723      /usr/bin/pidgin
09027000-09ad2000 rw-p 09027000 00:00 0          [heap]
afdce000-afe61000 rw-p afdce000 00:00 0 
afe61000-afe92000 r-xp 00000000 08:01 9506       /usr/lib/libcroco-0.6.so.3.0.1
afe92000-afe95000 rw-p 00030000 08:01 9506       /usr/lib/libcroco-0.6.so.3.0.1
afe95000-afec8000 r-xp 00000000 08:01 9788       /usr/lib/libgsf-1.so.114.0.11
afec8000-afec9000 ---p 00033000 08:01 9788       /usr/lib/libgsf-1.so.114.0.11
afec9000-afecb000 r--p 00033000 08:01 9788       /usr/lib/libgsf-1.so.114.0.11
afecb000-afecc000 rw-p 00035000 08:01 9788       /usr/lib/libgsf-1.so.114.0.11
afecc000-afecd000 rw-p afecc000 00:00 0 
afecd000-afefe000 r-xp 00000000 08:01 32110      /usr/lib/librsvg-2.so.2.26.0
afefe000-afeff000 r--p 00031000 08:01 32110      /usr/lib/librsvg-2.so.2.26.0
afeff000-aff00000 rw-p 00032000 08:01 32110      /usr/lib/librsvg-2.so.2.26.0
aff00000-aff21000 rw-p aff00000 00:00 0 
aff21000-b0000000 ---p aff21000 00:00 0 
b001d000-b002c000 r-xp 00000000 08:01 2563       /lib/libbz2.so.1.0.4
b002c000-b002d000 r--p 0000f000 08:01 2563       /lib/libbz2.so.1.0.4
b002d000-b002e000 rw-p 00010000 08:01 2563       /lib/libbz2.so.1.0.4
b002e000-b002f000 r-xp 00000000 08:01 11255      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b002f000-b0030000 r--p 00000000 08:01 11255      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b0030000-b0031000 rw-p 00001000 08:01 11255      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b0031000-b0032000 ---p b0031000 00:00 0 
b0032000-b0832000 rw-p b0032000 00:00 0 
b0832000-b0833000 ---p b0832000 00:00 0 
b0833000-b1033000 rw-p b0833000 00:00 0 
b1033000-b5034000 rw-s 00000000 00:15 165499     /dev/shm/pulse-shm-3851147281
b5034000-b5091000 r-xp 00000000 08:01 49357      /usr/lib/libpulse.so.0.7.1
b5091000-b5092000 r--p 0005c000 08:01 49357      /usr/lib/libpulse.so.0.7.1
b5092000-b5093000 rw-p 0005d000 08:01 49357      /usr/lib/libpulse.so.0.7.1
b5093000-b5156000 r-xp 00000000 08:01 51826      /usr/lib/libasound.so.2.0.0
b5156000-b5158000 r--p 000c2000 08:01 51826      /usr/lib/libasound.so.2.0.0
b5158000-b515b000 rw-p 000c4000 08:01 51826      /usr/lib/libasound.so.2.0.0
b5174000-b5177000 r-xp 00000000 08:01 216293     /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5177000-b5178000 r--p 00002000 08:01 216293     /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5178000-b5179000 rw-p 00003000 08:01 216293     /usr/lib/libcanberra-0.11/libcanberra-alsa.so
b5179000-b51d9000 rw-s 00000000 00:09 4882456    /SYSV00000000 (deleted)
b51d9000-b5239000 rw-s 00000000 00:09 4849687    /SYSV00000000 (deleted)
b5239000-b52c5000 r--p 00000000 08:01 42377      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b52c5000-b52c6000 r-xp 00000000 08:01 408240     /usr/lib/gconv/ISO8859-1.so
b52c6000-b52c7000 r--p 00001000 08:01 408240     /usr/lib/gconv/ISO8859-1.so
b52c7000-b52c8000 rw-p 00002000 08:01 408240     /usr/lib/gconv/ISO8859-1.so
b52c8000-b5397000 rw-p b52c8000 00:00 0 
b5397000-b53d6000 r-xp 00000000 08:01 51749      /usr/lib/libhunspell-1.2.so.0.0.0
b53d6000-b53d7000 r--p 0003e000 08:01 51749      /usr/lib/libhunspell-1.2.so.0.0.0
b53d7000-b53db000 rw-p 0003f000 08:01 51749      /usr/lib/libhunspell-1.2.so.0.0.0
b53de000-b53e2000 r-xp 00000000 08:01 2556       /lib/libattr.so.1.1.0
b53e2000-b53e3000 r--p 00003000 08:01 2556       /lib/libattr.so.1.1.0
b53e3000-b53e4000 rw-p 00004000 08:01 2556       /lib/libattr.so.1.1.0
b53e4000-b53e9000 r-xp 00000000 08:01 9650       /usr/lib/libgdbm.so.3.0.0
b53e9000-b53ea000 r--p 00004000 08:01 9650       /usr/lib/libgdbm.so.3.0.0
b53ea000-b53eb000 rw-p 00005000 08:01 9650       /usr/lib/libgdbm.so.3.0.0
b53eb000-b53ee000 r-xp 00000000 08:01 2569       /lib/libcap.so.2.11
b53ee000-b53ef000 r--p 00002000 08:01 2569       /lib/libcap.so.2.11
b53ef000-b53f0000 rw-p 00003000 08:01 2569       /lib/libcap.so.2.11
b53f0000-b53f2000 r-xp 00000000 08:01 11342      /usr/lib/enchant/libenchant_zemberek.so
b53f2000-b53f3000 r--p 00001000 08:01 11342      /usr/lib/enchant/libenchant_zemberek.so
b53f3000-b53f4000 rw-p 00002000 08:01 11342      /usr/lib/enchant/libenchant_zemberek.so
b53f4000-b5488000 r-xp 00000000 08:01 9419       /usr/lib/libaspell.so.15.1.4
b5488000-b548b000 r--p 00093000 08:01 9419       /usr/lib/libaspell.so.15.1.4
b548b000-b548c000 rw-p 00096000 08:01 9419       /usr/lib/libaspell.so.15.1.4
b548c000-b5490000 rw-p b548c000 00:00 0 
b5490000-b549d000 r-xp 00000000 08:01 81636      /lib/libgcc_s.so.1
b549d000-b549e000 r--p 0000c000 08:01 81636      /lib/libgcc_s.so.1
b549e000-b549f000 rw-p 0000d000 08:01 81636      /lib/libgcc_s.so.1
b549f000-b5583000 r-xp 00000000 08:01 14584      /usr/lib/libstdc++.so.6.0.10
b5583000-b5587000 r--p 000e3000 08:01 14584      /usr/lib/libstdc++.so.6.0.10
b5587000-b5588000 rw-p 000e7000 08:01 14584      /usr/lib/libstdc++.so.6.0.10
b5588000-b558e000 rw-p b5588000 00:00 0 
b558f000-b5594000 r-xp 00000000 08:01 10612      /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b5594000-b5595000 r--p 00004000 08:01 10612      /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b5595000-b5596000 rw-p 00005000 08:01 10612      /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b5596000-b559e000 r-xp 00000000 08:01 11339      /usr/lib/enchant/libenchant_hspell.so
b559e000-b559f000 r--p 00007000 08:01 11339      /usr/lib/enchant/libenchant_hspell.so
b559f000-b55a1000 rw-p 00008000 08:01 11339      /usr/lib/enchant/libenchant_hspell.so
b55a1000-b55a5000 r-xp 00000000 08:01 11341      /usr/lib/enchant/libenchant_myspell.so
b55a5000-b55a6000 r--p 00003000 08:01 11341      /usr/lib/enchant/libenchant_myspell.so
b55a6000-b55a7000 rw-p 00004000 08:01 11341      /usr/lib/enchant/libenchant_myspell.so
b55a7000-b55b2000 r-xp 00000000 08:01 11340      /usr/lib/enchant/libenchant_ispell.so
b55b2000-b55b3000 r--p 0000a000 08:01 11340      /usr/lib/enchant/libenchant_ispell.so
b55b3000-b55b4000 rw-p 0000b000 08:01 11340      /usr/lib/enchant/libenchant_ispell.so
b55b4000-b55b6000 r-xp 00000000 08:01 20541      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b55b6000-b55b7000 r--p 00001000 08:01 20541      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b55b7000-b55b8000 rw-p 00002000 08:01 20541      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b55b8000-b5650000 r--p 00000000 08:01 42378      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5650000-b5656000 r--s 00000000 08:01 52752      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5656000-b565b000 r--s 00000000 08:01 1442483    /var/cache/fontconfig/e25ca923d7a08ab6b0777bd7eb77ea77-x86.cache-2
b565b000-b565e000 r--s 00000000 08:01 1442482    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b565e000-b5661000 r--s 00000000 08:01 1442467    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b5661000-b5665000 r--s 00000000 08:01 1442481    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5665000-b5668000 r--s 00000000 08:01 1442480    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b5668000-b5669000 r--s 00000000 08:01 1442479    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5669000-b566c000 r--s 00000000 08:01 1442478    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b566c000-b5673000 r--s 00000000 08:01 1442477    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5673000-b567b000 r--s 00000000 08:01 1442475    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b567b000-b5686000 r--s 00000000 08:01 1442474    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5686000-b56a8000 r--s 00000000 08:01 1442471    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b56a8000-b56c3000 r--s 00000000 08:01 15236      /usr/share/mime/mime.cache
b56c3000-b56dd000 r-xp 00000000 08:01 7105       /usr/lib/gio/modules/libgvfsdbus.so
b56dd000-b56de000 r--p 00019000 08:01 7105       /usr/lib/gio/modules/libgvfsdbus.Aborted (core dumped)

```
Anyone know how to fix it??

---

### Post by linux_lover69 on 2009-04-06
Bump

---

### Post by linux_lover69 on 2009-04-06
Anyone? I really would like to get it to work.

---

### Post by linux_lover69 on 2009-04-08
Ok well I found out what was wrong. Its a bug. :mad:

---

### Post by MaX on 2009-04-08
> **linux_lover69 said:**
> Ok well I found out what was wrong. Its a bug. :mad:
So did you report the bug?
Was it already reported?

What did this have to do with Jaunty?
The first post in the help section of [Gfire's forum]("http://sourceforge.net/forum/forum.php?thread_id=3124923&forum_id=474407") had the solution for you.

---

### Post by linux_lover69 on 2009-04-08
The bug was already reported, one of the developer guys said its a problem with Jaunty and when 0.8.1 is released it will be fixed. Oh and the solution didn't work for me. I was already searching through that forum.

---

### Post by cariboo on 2009-04-08
never mind.

Jim

---

