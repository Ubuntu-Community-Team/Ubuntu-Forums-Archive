---
title: "Can't open Nautilus with root privileges in Karmic"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nechus on 2009-08-28
Tried to open Nautilus with root privileges from the terminal and got this:

nelson@nechus:~$ sudo nautilus
** Message: Initializing gksu extension...

** (nautilus:4275): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4275): WARNING **: No marshaller for signature of signal 'DownloadFinished'
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x01 0x00 0x00 0x00 0x00 0x00 
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
Fallo de segmentación (core dumped)
nelson@nechus:~$ 

What can I do?
Thanks

---

### Post by ad_267 on 2009-08-28
You should run graphical applications with "gksudo"
```
gksudo nautilus
```

---

### Post by nechus on 2009-08-28
Thanks for replying so promptly. I did what you said but Nautilus didn't open and I got this loooooong message:

```
0054a000-00551000 r-xp 00000000 08:05 5235045    /usr/lib/libgailutil.so.18.0.1
00551000-00552000 r--p 00006000 08:05 5235045    /usr/lib/libgailutil.so.18.0.1
00552000-00553000 rw-p 00007000 08:05 5235045    /usr/lib/libgailutil.so.18.0.1
00553000-00583000 r-xp 00000000 08:05 8388729    /lib/libpcre.so.3.12.1
00583000-00584000 r--p 0002f000 08:05 8388729    /lib/libpcre.so.3.12.1
00584000-00585000 rw-p 00030000 08:05 8388729    /lib/libpcre.so.3.12.1
00585000-00587000 r-xp 00000000 08:05 5235010    /usr/lib/libXau.so.6.0.0
00587000-00588000 r--p 00001000 08:05 5235010    /usr/lib/libXau.so.6.0.0
00588000-00589000 rw-p 00002000 08:05 5235010    /usr/lib/libXau.so.6.0.0
00589000-0058d000 r-xp 00000000 08:05 6555580    /usr/lib/libXdmcp.so.6.0.0
0058d000-0058e000 rw-p 00003000 08:05 6555580    /usr/lib/libXdmcp.so.6.0.0
0058e000-00590000 r-xp 00000000 08:05 6619170    /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so
00590000-00591000 r--p 00001000 08:05 6619170    /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so
00591000-00592000 rw-p 00002000 08:05 6619170    /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so
00592000-005af000 r-xp 00000000 08:05 8388915    /lib/ld-2.10.1.so
005af000-005b0000 r--p 0001c000 08:05 8388915    /lib/ld-2.10.1.so
005b0000-005b1000 rw-p 0001d000 08:05 8388915    /lib/ld-2.10.1.so
005b1000-0062b000 r-xp 00000000 08:05 5235004    /usr/lib/libfreetype.so.6.3.20
0062b000-0062f000 r--p 00079000 08:05 5235004    /usr/lib/libfreetype.so.6.3.20
0062f000-00630000 rw-p 0007d000 08:05 5235004    /usr/lib/libfreetype.so.6.3.20
00630000-00642000 r-xp 00000000 08:05 8413274    /lib/tls/i686/cmov/libresolv-2.10.1.so
00642000-00643000 r--p 00011000 08:05 8413274    /lib/tls/i686/cmov/libresolv-2.10.1.so
00643000-00644000 rw-p 00012000 08:05 8413274    /lib/tls/i686/cmov/libresolv-2.10.1.so
00644000-00646000 rw-p 00000000 00:00 0 
00646000-0065c000 r-xp 00000000 08:05 5234996    /usr/lib/libdirect-1.2.so.0.7.0
0065c000-0065d000 r--p 00015000 08:05 5234996    /usr/lib/libdirect-1.2.so.0.7.0
0065d000-0065e000 rw-p 00016000 08:05 5234996    /usr/lib/libdirect-1.2.so.0.7.0
0065e000-00660000 r-xp 00000000 08:05 8413259    /lib/tls/i686/cmov/libdl-2.10.1.so
00660000-00661000 r--p 00002000 08:05 8413259    /lib/tls/i686/cmov/libdl-2.10.1.so
00661000-00662000 rw-p 00003000 08:05 8413259    /lib/tls/i686/cmov/libdl-2.10.1.so
00662000-00669000 r-xp 00000000 08:05 8413263    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
00669000-0066a000 r--p 00006000 08:05 8413263    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
0066a000-0066b000 rw-p 00007000 08:05 8413263    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
0066b000-0066d000 r-xp 00000000 08:05 8413286    /lib/tls/i686/cmov/libutil-2.10.1.so
0066d000-0066e000 r--p 00001000 08:05 8413286    /lib/tls/i686/cmov/libutil-2.10.1.so
0066e000-0066f000 rw-p 00002000 08:05 8413286    /lib/tls/i686/cmov/libutil-2.10.1.so
0066f000-00671000 r-xp 00000000 08:05 6621427    /usr/lib/nautilus/extensions-2.0/libnautilus-seahorse.so
00671000-00672000 r--p 00001000 08:05 6621427    /usr/lib/nautilus/extensions-2.0/libnautilus-seahorse.so
00672000-00673000 rw-p 00002000 08:05 6621427    /usr/lib/nautilus/extensions-2.0/libnautilus-seahorse.so
00673000-00674000 r-xp 00000000 00:00 0          [vdso]
00674000-006b8000 r-xp 00000000 08:05 5235006    /usr/lib/libpixman-1.so.0.14.0
006b8000-006ba000 r--p 00043000 08:05 5235006    /usr/lib/libpixman-1.so.0.14.0
006ba000-006bb000 rw-p 00045000 08:05 5235006    /usr/lib/libpixman-1.so.0.14.0
006bb000-006e1000 r-xp 00000000 08:05 5235008    /usr/lib/libpng12.so.0.37.0
006e1000-006e2000 r--p 00025000 08:05 5235008    /usr/lib/libpng12.so.0.37.0
006e2000-006e3000 rw-p 00026000 08:05 5235008    /usr/lib/libpng12.so.0.37.0
006e3000-006ff000 r-xp 00000000 08:05 5235012    /usr/lib/libxcb.so.1.1.0
006ff000-00700000 r--p 0001c000 08:05 5235012    /usr/lib/libxcb.so.1.1.0
00700000-00701000 rw-p 0001d000 08:05 5235012    /usr/lib/libxcb.so.1.1.0
00701000-00704000 r-xp 00000000 08:05 6555914    /usr/lib/libavahi-glib.so.1.0.1
00704000-00705000 r--p 00002000 08:05 6555914    /usr/lib/libavahi-glib.so.1.0.1
00705000-00706000 rw-p 00003000 08:05 6555914    /usr/lib/libavahi-glib.so.1.0.1
00706000-00709000 r-xp 00000000 08:05 6556411    /usr/lib/liblaunchpad-integration.so.1.0.0
00709000-0070a000 r--p 00002000 08:05 6556411    /usr/lib/liblaunchpad-integration.so.1.0.0
0070a000-0070b000 rw-p 00003000 08:05 6556411    /usr/lib/liblaunchpad-integration.so.1.0.0
0070b000-007ef000 r-xp 00000000 08:05 6553844    /usr/lib/libexempi.so.3.2.1
007ef000-007f0000 ---p 000e4000 08:05 6553844    /usr/lib/libexempi.so.3.2.1
007f0000-007f3000 r--p 000e4000 08:05 6553844    /usr/lib/libexempi.so.3.2.1
007f3000-007f5000 rw-p 000e7000 08:05 6553844    /usr/lib/libexempi.so.3.2.1
007f5000-00819000 r-xp 00000000 08:05 6555875    /usr/lib/libexpat.so.1.5.2
00819000-0081b000 r--p 00023000 08:05 6555875    /usr/lib/libexpat.so.1.5.2
0081b000-0081c000 rw-p 00025000 08:05 6555875    /usr/lib/libexpat.so.1.5.2
0081c000-00831000 r-xp 00000000 08:05 8413262    /lib/tls/i686/cmov/libnsl-2.10.1.so
00831000-00832000 r--p 00014000 08:05 8413262    /lib/tls/i686/cmov/libnsl-2.10.1.so
00832000-00833000 rw-p 00015000 08:05 8413262    /lib/tls/i686/cmov/libnsl-2.10.1.so
00833000-00835000 rw-p 00000000 00:00 0 
00835000-00840000 r-xp 00000000 08:05 8413265    /lib/tls/i686/cmov/libnss_files-2.10.1.so
00840000-00841000 r--p 0000a000 08:05 8413265    /lib/tls/i686/cmov/libnss_files-2.10.1.so
00841000-00842000 rw-p 0000b000 08:05 8413265    /lib/tls/i686/cmov/libnss_files-2.10.1.so
00845000-0088b000 r-xp 00000000 08:05 6553826    /usr/lib/libpango-1.0.so.0.2503.0
0088b000-0088c000 r--p 00046000 08:05 6553826    /usr/lib/libpango-1.0.so.0.2503.0
0088c000-0088d000 rw-p 00047000 08:05 6553826    /usr/lib/libpango-1.0.so.0.2503.0
0088d000-00891000 r-xp 00000000 08:05 6555503    /usr/lib/libORBitCosNaming-2.so.0.1.0
00891000-00892000 r--p 00003000 08:05 6555503    /usr/lib/libORBitCosNaming-2.so.0.1.0
00892000-00893000 rw-p 00004000 08:05 6555503    /usr/lib/libORBitCosNaming-2.so.0.1.0
00894000-0089d000 r-xp 00000000 08:05 5235041    /usr/lib/libXi.so.6.0.0
0089d000-0089e000 r--p 00008000 08:05 5235041    /usr/lib/libXi.so.6.0.0
0089e000-0089f000 rw-p 00009000 08:05 5235041    /usr/lib/libXi.so.6.0.0
0089f000-008a2000 r-xp 00000000 08:05 8388668    /lib/libgpg-error.so.0.4.0
008a2000-008a3000 r--p 00002000 08:05 8388668    /lib/libgpg-error.so.0.4.0
008a3000-008a4000 rw-p 00003000 08:05 8388668    /lib/libgpg-error.so.0.4.0
008a7000-008c1000 r-xp 00000000 08:05 5235078    /usr/lib/libgdk_pixbuf-2.0.so.0.1707.0
008c1000-008c2000 r--p 0001a000 08:05 5235078    /usr/lib/libgdk_pixbuf-2.0.so.0.1707.0
008c2000-008c3000 rw-p 0001b000 08:05 5235078    /usr/lib/libgdk_pixbuf-2.0.so.0.1707.0
008c3000-008ed000 r-xp 00000000 08:05 8388618    /lib/libgcc_s.so.1
008ed000-008ee000 r--p 00029000 08:05 8388618    /lib/libgcc_s.so.1
008ee000-008ef000 rw-p 0002a000 08:05 8388618    /lib/libgcc_s.so.1
008f3000-008f6000 r-xp 00000000 08:05 5234984    /usr/lib/libgmodule-2.0.so.0.2105.0
008f6000-008f7000 r--p 00002000 08:05 5234984    /usr/lib/libgmodule-2.0.so.0.2105.0
008f7000-008f8000 rw-p 00003000 08:05 5234984    /usr/lib/libgmodule-2.0.so.0.2105.0
008f8000-008fc000 r-xp 00000000 08:05 6555610    /usr/lib/libXtst.so.6.1.0
008fc000-008fd000 r--p 00004000 08:05 6555610    /usr/lib/libXtst.so.6.1.0
008fd000-008fe000 rw-p 00005000 08:05 6555610    /usr/lib/libXtst.so.6.1.0
008fe000-00905000 r-xp 00000000 08:05 5235016    /usr/lib/libxcb-render.so.0.0.0
00905000-00906000 r--p 00007000 08:05 5235016    /usr/lib/libxcb-render.so.0.0.0
00906000-00907000 rw-p 00008000 08:05 5235016    /usr/lib/libxcb-render.so.0.0.0
00907000-0090f000 r-xp 00000000 08:05 6595016    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
0090f000-00910000 r--p 00007000 08:05 6595016    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00910000-00911000 rw-p 00008000 08:05 6595016    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00911000-00916000 r-xp 00000000 08:05 6555527    /usr/lib/libgstvideo-0.10.so.0.17.0
00916000-00917000 r--p 00005000 08:05 6555527    /usr/lib/libgstvideo-0.10.so.0.17.0
00917000-00918000 rw-p 00006000 08:05 6555527    /usr/lib/libgstvideo-0.10.so.0.17.0
00919000-00927000 r-xp 00000000 08:05 6555582    /usr/lib/libXext.so.6.4.0
00927000-00928000 r--p 0000d000 08:05 6555582    /usr/lib/libXext.so.6.4.0
00928000-00929000 rw-p 0000e000 08:05 6555582    /usr/lib/libXext.so.6.4.0
00929000-00972000 r-xp 00000000 08:05 6555499    /usr/lib/libORBit-2.so.0.1.0
00972000-0097a000 r--p 00049000 08:05 6555499    /usr/lib/libORBit-2.so.0.1.0
0097a000-0097c000 rw-p 00051000 08:05 6555499    /usr/lib/libORBit-2.so.0.1.0
0097c000-00980000 r-xp 00000000 08:05 6555622    /usr/lib/libXxf86vm.so.1.0.0
00980000-00981000 r--p 00003000 08:05 6555622    /usr/lib/libXxf86vm.so.1.0.0
00981000-00982000 rw-p 00004000 08:05 6555622    /usr/lib/libXxf86vm.so.1.0.0
00982000-00989000 r-xp 00000000 08:05 5235043    /usr/lib/libXrandr.so.2.2.0
00989000-0098a000 r--p 00006000 08:05 5235043    /usr/lib/libXrandr.so.2.2.0
0098a000-0098b000 rw-p 00007000 08:05 5235043    /usr/lib/libXrandr.so.2.2.0
0098b000-00997000 r-xp 00000000 08:05 6594634    /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
00997000-00998000 r--p 0000b000 08:05 6594634    /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
00998000-00999000 rw-p 0000c000 08:05 6594634    /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
00999000-009ad000 r-xp 00000000 08:05 6555177    /usr/lib/libgnome-keyring.so.0.1.1
009ad000-009ae000 r--p 00013000 08:05 6555177    /usr/lib/libgnome-keyring.so.0.1.1
009ae000-009af000 rw-p 00014000 08:05 6555177    /usr/lib/libgnome-keyring.so.0.1.1
009af000-009bf000 r-xp 00000000 08:05 6553805    /usr/lib/libgtop-2.0.so.7.2.0
009bf000-009c0000 r--p 0000f000 08:05 6553805    /usr/lib/libgtop-2.0.so.7.2.0
009c0000-009c1000 rw-p 00010000 08:05 6553805    /usr/lib/libgtop-2.0.so.7.2.0
009c3000-009d8000 r-xp 00000000 08:05 6555951    /usr/lib/libgvfscommon.so.0.0.0
009d8000-009d9000 r--p 00014000 08:05 6555951    /usr/lib/libgvfscommon.so.0.0.0
009d9000-009da000 rw-p 00015000 08:05 6555951    /usr/lib/libgvfscommon.so.0.0.0
009da000-009ed000 r-xp 00000000 08:05 6594928    /usr/lib/gio/modules/libgioremote-volume-monitor.so
009ed000-009ee000 r--p 00012000 08:05 6594928    /usr/lib/gio/modules/libgioremote-volume-monitor.so
009ee000-009ef000 rw-p 00013000 08:05 6594928    /usr/lib/gio/modules/libgioremote-volume-monitor.so
009ef000-009f7000 r-xp 00000000 08:05 8388733    /lib/libpopt.so.0.0.0
009f7000-009f8000 r--p 00007000 08:05 8388733    /lib/libpopt.so.0.0.0
009f8000-009f9000 rw-p 00008000 08:05 8388733    /lib/libpopt.so.0.0.0
009f9000-00a14000 r-xp 00000000 08:05 5234988    /usr/lib/libatk-1.0.so.0.2799.1
00a14000-00a15000 r--p 0001b000 08:05 5234988    /usr/lib/libatk-1.0.so.0.2799.1
00a15000-00a16000 rw-p 0001c000 08:05 5234988    /usr/lib/libatk-1.0.so.0.2799.1
00a16000-00a20000 r-xp 00000000 08:05 6619375    /usr/lib/nautilus/extensions-2.0/libnautilus-share.so
00a20000-00a21000 r--p 00009000 08:05 6619375    /usr/lib/nautilus/extensions-2.0/libnautilus-share.so
00a21000-00a22000 rw-p 0000a000 08:05 6619375    /usr/lib/nautilus/extensions-2.0/libnautilus-share.so
00a22000-00a7c000 r-xp 00000000 08:05 6555700    /usr/lib/libbonoboui-2.so.0.0.0
00a7c000-00a7d000 r--p 0005a000 08:05 6555700    /usr/lib/libbonoboui-2.so.0.0.0
00a7d000-00a7f000 rw-p 0005b000 08:05 6555700    /usr/lib/libbonoboui-2.so.0.0.0
00a81000-00a85000 r-xp 00000000 08:05 5234986    /usr/lib/libgthread-2.0.so.0.2105.0
00a85000-00a86000 r--p 00003000 08:05 5234986    /usr/lib/libgthread-2.0.so.0.2105.0
00a86000-00a87000 rw-p 00004000 08:05 5234986    /usr/lib/libgthread-2.0.so.0.2105.0
00a87000-00a91000 r-xp 00000000 08:05 6554160    /usr/lib/libesd.so.0.2.39
00a91000-00a92000 r--p 00009000 08:05 6554160    /usr/lib/libesd.so.0.2.39
00a92000-00a93000 rw-p 0000a000 08:05 6554160    /usr/lib/libesd.so.0.2.39
00a93000-00a98000 r-xp 00000000 08:05 6619180    /usr/lib/nautilus/extensions-2.0/libnautilus-ubuntuone.so
00a98000-00a99000 r--p 00004000 08:05 6619180    /usr/lib/nautilus/extensions-2.0/libnautilus-ubuntuone.so
00a99000-00a9a000 rw-p 00005000 08:05 6619180    /usr/lib/nautilus/extensions-2.0/libnautilus-ubuntuone.so
00a9c000-00ac3000 r-xp 00000000 08:05 6556025    /usr/lib/libexif.so.12.2.1
00ac3000-00acd000 r--p 00027000 08:05 6556025    /usr/lib/libexif.so.12.2.1
00acd000-00ace000 rw-p 00031000 08:05 6556025    /usr/lib/libexif.so.12.2.1
00ace000-00b01000 r-xp 00000000 08:05 6555187    /usr/lib/libgnomecanvas-2.so.0.2600.0
00b01000-00b02000 r--p 00032000 08:05 6555187    /usr/lib/libgnomecanvas-2.so.0.2600.0
00b02000-00b03000 rw-p 00033000 08:05 6555187    /usr/lib/libgnomecanvas-2.so.0.2600.0
00b03000-00b07000 r-xp 00000000 08:05 6619200    /usr/lib/nautilus/extensions-2.0/libevince-properties-page.so
00b07000-00b08000 r--p 00003000 08:05 6619200    /usr/lib/nautilus/extensions-2.0/libevince-properties-page.so
00b08000-00b09000 rw-p 00004000 08:05 6619200    /usr/lib/nautilus/extensions-2.0/libevince-properties-page.so
00b0c000-00bb9000 r-xp 00000000 08:05 6554017    /usr/lib/libgio-2.0.so.0.2105.0
00bb9000-00bba000 ---p 000ad000 08:05 6554017    /usr/lib/libgio-2.0.so.0.2105.0
00bba000-00bbb000 r--p 000ad000 08:05 6554017    /usr/lib/libgio-2.0.so.0.2105.0
00bbb000-00bbc000 rw-p 000ae000 08:05 6554017    /usr/lib/libgio-2.0.so.0.2105.0
00bbc000-00bbd000 rw-p 00000000 00:00 0 
00bc2000-00c02000 r-xp 00000000 08:05 8388658    /lib/libdbus-1.so.3.4.0
00c02000-00c03000 r--p 0003f000 08:05 8388658    /lib/libdbus-1.so.3.4.0
00c03000-00c04000 rw-p 00040000 08:05 8388658    /lib/libdbus-1.so.3.4.0
00c04000-00c0d000 r-xp 00000000 08:05 6619184    /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
00c0d000-00c0e000 r--p 00008000 08:05 6619184    /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
00c0e000-00c0f000 rw-p 00009000 08:05 6619184    /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
00c0f000-00c1f000 r-xp 00000000 08:05 6554426    /usr/lib/libgksu2.so.0.0.2
00c1f000-00c20000 r--p 0000f000 08:05 6554426    /usr/lib/libgksu2.so.0.0.2
00c20000-00c21000 rw-p 00010000 08:05 6554426    /usr/lib/libgksu2.so.0.0.2
00c2d000-00c44000 r-xp 00000000 08:05 6553602    /usr/lib/libICE.so.6.3.0
00c44000-00c45000 r--p 00016000 08:05 6553602    /usr/lib/libICE.so.6.3.0
00c45000-00c46000 rw-p 00017000 08:05 6553602    /usr/lib/libICE.so.6.3.0
00c46000-00c48000 rw-p 00000000 00:00 0 
00c48000-00c5d000 r-xp 00000000 08:05 6555618    /usr/lib/libgnome-2.so.0.2704.1
00c5d000-00c5e000 ---p 00015000 08:05 6555618    /usr/lib/libgnome-2.so.0.2704.1
00c5e000-00c5f000 r--p 00015000 08:05 6555618    /usr/lib/libgnome-2.so.0.2704.1
00c5f000-00c60000 rw-p 00016000 08:05 6555618    /usr/lib/libgnome-2.so.0.2704.1
00c60000-00c75000 r-xp 00000000 08:05 6555642    /usr/lib/libart_lgpl_2.so.2.3.20
00c75000-00c77000 rw-p 00014000 08:05 6555642    /usr/lib/libart_lgpl_2.so.2.3.20
00c81000-00cc5000 r-xp 00000000 08:05 5234985    /usr/lib/libgobject-2.0.so.0.2105.0
00cc5000-00cc6000 r--p 00044000 08:05 5234985    /usr/lib/libgobject-2.0.so.0.2105.0
00cc6000-00cc7000 rw-p 00045000 08:05 5234985    /usr/lib/libgobject-2.0.so.0.2105.0
00cc7000-00d19000 r-xp 00000000 08:05 6555696    /usr/lib/libbonobo-2.so.0.0.0
00d19000-00d1c000 r--p 00051000 08:05 6555696    /usr/lib/libbonobo-2.so.0.0.0
00d1c000-00d23000 rw-p 00054000 08:05 6555696    /usr/lib/libbonobo-2.so.0.0.0
00d26000-00d2d000 r-xp 00000000 08:05 6554090    /usr/lib/libSM.so.6.0.0
00d2d000-00d2e000 r--p 00006000 08:05 6554090    /usr/lib/libSM.so.6.0.0
00d2e000-00d2f000 rw-p 00007000 08:05 6554090    /usr/lib/libSM.so.6.0.0
00d2f000-00d42000 r-xp 00000000 08:05 6555698    /usr/lib/libbonobo-activation.so.4.0.0
00d42000-00d43000 r--p 00012000 08:05 6555698    /usr/lib/libbonobo-activation.so.4.0.0
00d43000-00d44000 rw-p 00013000 08:05 6555698    /usr/lib/libbonobo-activation.so.4.0.0
00d44000-00d45000 rw-p 00000000 00:00 0 
00d49000-00dcd000 r-xp 00000000 08:05 5235020    /usr/lib/libcairo.so.2.10800.8
00dcd000-00dcf000 r--p 00083000 08:05 5235020    /usr/lib/libcairo.so.2.10800.8
00dcf000-00dd0000 rw-p 00085000 08:05 5235020    /usr/lib/libcairo.so.2.10800.8
00dd0000-00ddb000 r-xp 00000000 08:05 5235047    /usr/lib/libavahi-common.so.3.5.1
00ddb000-00ddc000 r--p 0000a000 08:05 5235047    /usr/lib/libavahi-common.so.3.5.1
00ddc000-00ddd000 rw-p 0000b000 08:05 5235047    /usr/lib/libavahi-common.so.3.5.1
00ddd000-00dec000 r-xp 00000000 08:05 5235049    /usr/lib/libavahi-client.so.3.2.5
00dec000-00ded000 r--p 0000f000 08:05 5235049    /usr/lib/libavahi-client.so.3.2.5
00ded000-00dee000 rw-p 00010000 08:05 5235049    /usr/lib/libavahi-client.so.3.2.5
00df8000-00e14000 r-xp 00000000 08:05 8388638    /lib/libselinux.so.1
00e14000-00e15000 r--p 0001b000 08:05 8388638    /lib/libselinux.so.1
00e15000-00e16000 rw-p 0001c000 08:05 8388638    /lib/libselinux.so.1
00e16000-00f40000 r-xp 00000000 08:05 5235014    /usr/lib/libX11.so.6.2.0
00f40000-00f41000 ---p 0012a000 08:05 5235014    /usr/lib/libX11.so.6.2.0
00f41000-00f42000 r--p 0012a000 08:05 5235014    /usr/lib/libX11.so.6.2.0
00f42000-00f44000 rw-p 0012b000 08:05 5235014    /usr/lib/libX11.so.6.2.0
00f44000-00f45000 rw-p 00000000 00:00 0 
00f45000-00f6b000 r-xp 00000000 08:05 6553756    /usr/lib/libaudiofile.so.0.0.2
00f6b000-00f6c000 ---p 00026000 08:05 6553756    /usr/lib/libaudiofile.so.0.0.2
00f6c000-00f6d000 r--p 00026000 08:05 6553756    /usr/lib/libaudiofile.so.0.0.2
00f6d000-00f6f000 rw-p 00027000 08:05 6553756    /usr/lib/libaudiofile.so.0.0.2
00f6f000-00f7e000 r-xp 00000000 08:05 6555526    /usr/lib/libgsttag-0.10.so.0.17.0
00f7e000-00f7f000 r--p 0000e000 08:05 6555526    /usr/lib/libgsttag-0.10.so.0.17.0
00f7f000-00f80000 rw-p 0000f000 08:05 6555526    /usr/lib/libgsttag-0.10.so.0.17.0
00f80000-00f8b000 r-xp 00000000 08:05 6556452    /usr/lib/libunique-1.0.so.0.2.6
00f8b000-00f8c000 r--p 0000a000 08:05 6556452    /usr/lib/libunique-1.0.so.0.2.6
00f8c000-00f8d000 rw-p 0000b000 08:05 6556452    /usr/lib/libunique-1.0.so.0.2.6
00f8e000-00f97000 r-xp 00000000 08:05 8413267    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
00f97000-00f98000 r--p 00008000 08:05 8413267    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
00f98000-00f99000 rw-p 00009000 08:05 8413267    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
00f99000-00fa9000 r-xp 00000000 08:05 5235051    /usr/lib/libtasn1.so.3.1.5
00fa9000-00faa000 r--p 0000f000 08:05 5235051    /usr/lib/libtasn1.so.3.1.5
00faa000-00fab000 rw-p 00010000 08:05 5235051    /usr/lib/libtasn1.so.3.1.5
00fb0000-00fce000 r-xp 00000000 08:05 6553636    /usr/lib/libdbus-glib-1.so.2.1.0
00fce000-00fcf000 r--p 0001e000 08:05 6553636    /usr/lib/libdbus-glib-1.so.2.1.0
00fcf000-00fd0000 rw-p 0001f000 08:05 6553636    /usr/lib/libdbus-glib-1.so.2.1.0
00fd0000-01430000 r-xp 00000000 08:05 5235076    /usr/lib/libgtk-x11-2.0.so.0.1707.0
01430000-01431000 ---p 00460000 08:05 5235076    /usr/lib/libgtk-x11-2.0.so.0.1707.0
01431000-01435000 r--p 00460000 08:05 5235076    /usr/lib/libgtk-x11-2.0.so.0.1707.0
01435000-01437000 rw-p 00464000 08:05 5235076    /usr/lib/libgtk-x11-2.0.so.0.1707.0
01437000-01439000 rw-p 00000000 00:00 0 
01439000-0158a000 r-xp 00000000 08:05 8413253    /lib/tls/i686/cmov/libc-2.10.1.so
0158a000-0158b000 ---p 00151000 08:05 8413253    /lib/tls/i686/cmov/libc-2.10.1.so
0158b000-0158d000 r--p 00151000 08:05 8413253    /lib/tls/i686/cmov/libc-2.10.1.so
0158d000-0158e000 rw-p 00153000 08:05 8413253    /lib/tls/i686/cmov/libc-2.10.1.so
0158e000-01591000 rw-p 00000000 00:00 0 
01591000-01678000 r-xp 00000000 08:05 6553741    /usr/lib/libstdc++.so.6.0.13
01678000-0167c000 r--p 000e6000 08:05 6553741    /usr/lib/libstdc++.so.6.0.13
0167c000-0167d000 rw-p 000ea000 08:05 6553741    /usr/lib/libstdc++.so.6.0.13
0167d000-01684000 rw-p 00000000 00:00 0 
01684000-0170a000 r-xp 00000000 08:05 6556050    /usr/lib/libgnomeui-2.so.0.2400.1
0170a000-0170b000 ---p 00086000 08:05 6556050    /usr/lib/libgnomeui-2.so.0.2400.1
0170b000-0170d000 r--p 00086000 08:05 6556050    /usr/lib/libgnomeui-2.so.0.2400.1
0170d000-0170f000 rw-p 00088000 08:05 6556050    /usr/lib/libgnomeui-2.so.0.2400.1
0170f000-01732000 r-xp 00000000 08:05 6555687    /usr/lib/libbrasero-media.so.0.2.0
01732000-01733000 r--p 00022000 08:05 6555687    /usr/lib/libbrasero-media.so.0.2.0
01733000-01734000 rw-p 00023000 08:05 6555687    /usr/lib/libbrasero-media.so.0.2.0
01b8a000-01bac000 r-xp 00000000 08:05 6555509    /usr/lib/libgstaudio-0.10.so.0.17.0
01bac000-01bad000 ---p 00022000 08:05 6555509    /usr/lib/libgstaudio-0.10.so.0.17.0
01bad000-01bae000 r--p 00022000 08:05 6555509    /usr/lib/libgstaudio-0.10.so.0.17.0
01bae000-01baf000 rw-p 00023000 08:05 6555509    /usr/lib/libgstaudio-0.10.so.0.17.0
01ffe000-02018000 r-xp 00000000 08:05 6555802    /usr/lib/libevdocument.so.1.0.0
02018000-02019000 r--p 0001a000 08:05 6555802    /usr/lib/libevdocument.so.1.0.0
02019000-0201a000 rw-p 0001b000 08:05 6555802    /usr/lib/libevdocument.so.1.0.0
02922000-0296e000 r-xp 00000000 08:05 6553704    /usr/lib/libgmime-2.4.so.2.4.6
0296e000-0296f000 ---p 0004c000 08:05 6553704    /usr/lib/libgmime-2.4.so.2.4.6
0296f000-02971000 r--p 0004c000 08:05 6553704    /usr/lib/libgmime-2.4.so.2.4.6
02971000-02985000 rw-p 0004e000 08:05 6553704    /usr/lib/libgmime-2.4.so.2.4.6
02fcb000-02fd6000 r-xp 00000000 08:05 6555513    /usr/lib/libgstpbutils-0.10.so.0.17.0
02fd6000-02fd7000 ---p 0000b000 08:05 6555513    /usr/lib/libgstpbutils-0.10.so.0.17.0
02fd7000-02fd8000 r--p 0000b000 08:05 6555513    /usr/lib/libgstpbutils-0.10.so.0.17.0
02fd8000-02fd9000 rw-p 0000c000 08:05 6555513    /usr/lib/libgstpbutils-0.10.so.0.17.0
05a0e000-05aea000 r-xp 00000000 08:05 5235102    /usr/lib/libasound.so.2.0.0
05aea000-05aee000 r--p 000dc000 08:05 5235102    /usr/lib/libasound.so.2.0.0
05aee000-05aef000 rw-p 000e0000 08:05 5235102    /usr/lib/libasound.so.2.0.0
06323000-06348000 r-xp 00000000 08:05 6556842    /usr/lib/libbrasero-utils.so.0.2.0
06348000-06349000 r--p 00024000 08:05 6556842    /usr/lib/libbrasero-utils.so.0.2.0
06349000-0634a000 rw-p 00025000 08:05 6556842    /usr/lib/libbrasero-utils.so.0.2.0
0640a000-06448000 r-xp 00000000 08:05 6553813    /usr/lib/libgstbase-0.10.so.0.21.0
06448000-06449000 r--p 0003d000 08:05 6553813    /usr/lib/libgstbase-0.10.so.0.21.0
06449000-0644a000 rw-p 0003e000 08:05 6553813    /usr/lib/libgstbase-0.10.so.0.21.0
06b51000-06bf4000 r-xp 00000000 08:05 5235053    /usr/lib/libgnutls.so.26.14.10
06bf4000-06bf8000 r--p 000a2000 08:05 5235053    /usr/lib/libgnutls.so.26.14.10
06bf8000-06bf9000 rw-p 000a6000 08:05 5235053    /usr/lib/libgnutls.so.26.14.10
06cd5000-06d37000 r-xp 00000000 08:05 6554686    /usr/lib/libgnomevfs-2.so.0.2400.1
06d37000-06d39000 r--p 00061000 08:05 6554686    /usr/lib/libgnomevfs-2.so.0.2400.1
06d39000-06d3a000 rw-p 00063000 08:05 6554686    /usr/lib/libgnomevfs-2.so.0.2400.1
06d3a000-06d3b000 rw-p 00000000 00:00 0 
06d4d000-06dc6000 r-xp 00000000 08:05 8388679    /lib/libgcrypt.so.11.5.2
06dc6000-06dc7000 r--p 00078000 08:05 8388679    /lib/libgcrypt.so.11.5.2
06dc7000-06dc9000 rw-p 00079000 08:05 8388679    /lib/libgcrypt.so.11.5.2
07294000-0735e000 r-xp 00000000 08:05 6555507    /usr/lib/libgstreamer-0.10.so.0.21.0
0735e000-07361000 r--p 000c9000 08:05 6555507    /usr/lib/libgstreamer-0.10.so.0.21.0
07361000-07362000 rw-p 000cc000 08:05 6555507    /usr/lib/libgstreamer-0.10.so.0.21.0
07362000-07363000 rw-p 00000000 00:00 0 
0791d000-07935000 r-xp 00000000 08:05 6553715    /usr/lib/libtotem-plparser.so.12.4.4
07935000-07936000 r--p 00017000 08:05 6553715    /usr/lib/libtotem-plparser.so.12.4.4
07936000-07937000 rw-p 00018000 08:05 6553715    /usr/lib/libtotem-plparser.so.12.4.4
07c6c000-07c7a000 r-xp 00000000 08:05 6555520    /usr/lib/libgstinterfaces-0.10.so.0.17.0
07c7a000-07c7b000 r--p 0000e000 08:05 6555520    /usr/lib/libgstinterfaces-0.10.so.0.17.0
07c7b000-07c7c000 rw-p 0000f000 08:05 6555520    /usr/lib/libgstinterfaces-0.10.so.0.17.0
08048000-08207000 r-xp 00000000 08:05 6554800    /usr/bin/nautilus
08207000-08209000 r--p 001bf000 08:05 6554800    /usr/bin/nautilus
08209000-0820c000 rw-p 001c1000 08:05 6554800    /usr/bin/nautilus
0820c000-0820d000 rw-p 00000000 00:00 0 
0858e000-08610000 r-xp 00000000 08:05 6553717    /usr/lib/libbrasero-burn.so.0.2.0
08610000-08611000 r--p 00082000 08:05 6553717    /usr/lib/libbrasero-burn.so.0.2.0
08611000-08612000 rw-p 00083000 08:05 6553717    /usr/lib/libbrasero-burn.so.0.2.0
08675000-086eb000 r-xp 00000000 08:05 5234997    /usr/lib/libdirectfb-1.2.so.0.7.0
086eb000-086ec000 ---p 00076000 08:05 5234997    /usr/lib/libdirectfb-1.2.so.0.7.0
086ec000-086ed000 r--p 00076000 08:05 5234997    /usr/lib/libdirectfb-1.2.so.0.7.0
086ed000-086ee000 rw-p 00077000 08:05 5234997    /usr/lib/libdirectfb-1.2.so.0.7.0
086ee000-086ef000 rw-p 00000000 00:00 0 
08adc000-08b08000 r-xp 00000000 08:05 6619683    /usr/lib/nautilus/extensions-2.0/libtotem-properties-page.so
08b08000-08b09000 r--p 0002b000 08:05 6619683    /usr/lib/nautilus/extensions-2.0/libtotem-properties-page.so
08b09000-08b0a000 rw-p 0002c000 08:05 6619683    /usr/lib/nautilus/extensions-2.0/libtotem-properties-page.so
09315000-094be000 rw-p 00000000 00:00 0          [heap]
b6c00000-b6c21000 rw-p 00000000 00:00 0 
b6c21000-b6d00000 ---p 00000000 00:00 0 
b6dbb000-b6dbc000 rw-p 00000000 00:00 0 
b6dbc000-b6dd3000 r--p 00000000 08:05 6906043    /usr/share/locale-langpack/es/LC_MESSAGES/brasero.mo
b6dd3000-b6dda000 r--p 00000000 08:05 6906139    /usr/share/locale-langpack/es/LC_MESSAGES/gstreamer-0.10.mo
b6dda000-b6ddb000 ---p 00000000 00:00 0 
b6ddb000-b75db000 rw-p 00000000 00:00 0 
b75db000-b75dc000 ---p 00000000 00:00 0 
b75dc000-b7ddc000 rw-p 00000000 00:00 0 
b7ddc000-b7de8000 r--p 00000000 08:05 6906080    /usr/share/locale-langpack/es/LC_MESSAGES/glib20.mo
b7de8000-b7df9000 r--p 00000000 08:05 6906143    /usr/share/locale-langpack/es/LC_MESSAGES/GConf2.mo
b7df9000-b7e19000 r--p 00000000 08:05 6906240    /usr/share/locale-langpack/es/LC_MESSAGES/libc.mo
b7e19000-b7e42000 r--p 00000000 08:05 6906189    /usr/share/locale-langpack/es/LC_MESSAGES/gtk20-properties.mo
b7e42000-b7e54000 r--p 00000000 08:05 6906185    /usr/share/locale-langpack/es/LC_MESSAGES/gtk20.mo
b7e54000-b7e77000 r--p 00000000 08:05 6906097    /usr/share/locale-langpack/es/LC_MESSAGES/nautilus.mo
b7e77000-b7eb6000 r--p 00000000 08:05 6611374    /usr/lib/locale/es_CL.utf8/LC_CTYPE
b7eb6000-b7fa3000 r--p 00000000 08:05 6611432    /usr/lib/locale/es_CL.utf8/LC_COLLATE
b7fa3000-b7fb4000 rw-p 00000000 00:00 0 
b7fba000-b7fbb000 r--p 00000000 08:05 6611591    /usr/lib/locale/es_CL.utf8/LC_NUMERIC
b7fbb000-b7fbc000 r--p 00000000 08:05 6611671    /usr/lib/locale/es_CL.utf8/LC_TIME
b7fbc000-b7fbd000 r--p 00000000 08:05 6611431    /usr/lib/locale/es_CL.utf8/LC_MONETARY
b7fbd000-b7fbe000 r--p 00000000 08:05 6619160    /usr/lib/locale/es_CL.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fbe000-b7fbf000 r--p 00000000 08:05 6611713    /usr/lib/locale/es_CL.utf8/LC_PAPER
b7fbf000-b7fc0000 r--p 00000000 08:05 6611378    /usr/lib/locale/es_CL.utf8/LC_NAME
b7fc0000-b7fc1000 r--p 00000000 08:05 6611439    /usr/lib/locale/es_CL.utf8/LC_ADDRESS
b7fc1000-b7fc2000 r--p 00000000 08:05 6611440    /usr/lib/locale/es_CL.utf8/LC_TELEPHONE
b7fc2000-b7fc3000 r--p 00000000 08:05 6611376    /usr/lib/locale/es_CL.utf8/LC_MEASUREMENT
b7fc3000-b7fca000 r--s 00000000 08:05 6571684    /usr/lib/gconv/gconv-modules.cache
b7fca000-b7fcb000 r--p 00000000 08:05 6611441    /usr/lib/locale/es_CL.utf8/LC_IDENTIFICATION
b7fcb000-b7fcd000 rw-p 00000000 00:00 0 
bfadc000-bfaf1000 rw-p 00000000 00:00 0          [stack]
nelson@nechus:~$
```

---

### Post by corncob on 2009-08-28
Either way I can open Nautilus in Jaunty although I get several of these in the Terminal window: "Invalid borders specified for theme pixmap"  You might try typing "sudo su" to change to the root prompt and then typing "nautilus"  although it does the same thing for me.

---

### Post by meeples on 2009-08-28
i have this issue too.

---

### Post by handaxe on 2009-08-28
Just reported the crash and then seen this thread about it.  Report here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/420841](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/420841)

Please confirm and once thats done use the "this bug affects me" button.

HA

---

### Post by VMC on 2009-08-28
I'm not sure if mine is a bug or I missed installing something:

$ **gksudo nautilus**
```
Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x01 0x00 0x00 0x00 0x00 0x00 

** (nautilus:3053): WARNING **: No marshaller for signature of signal 'DownloadFinished'
```

---

### Post by MacUntu on 2009-08-28
Workaround: remove brasero.

---

### Post by nechus on 2009-08-28
> **MacUntu said:**
> Workaround: remove brasero.
Nope. Didn't work for me.

---

### Post by nechus on 2009-08-28
> **corncob said:**
> Either way I can open Nautilus in Jaunty although I get several of these in the Terminal window: "Invalid borders specified for theme pixmap"  You might try typing "sudo su" to change to the root prompt and then typing "nautilus"  although it does the same thing for me.

IT WORKED!!!!!!!!  Thank you!!!\\:D/

---

### Post by nechus on 2009-08-29
Thank you all for your help!

---

### Post by MacUntu on 2009-08-29
> **nechus said:**
> Nope. Didn't work for me.

Did you restart the Gnome session? Sorry, should have mentioned...

---

### Post by nechus on 2009-08-29
> **MacUntu said:**
> Did you restart the Gnome session? Sorry, should have mentioned...

Hello. I restarted the whole computer, but removing Brasero didn't seem to have an effect. Besides, corncob's suggestion worked only once. I have the same problem again and typing *sudo su* and then *nautilus* won't fix it anymore.:confused: Ain't it weird?

---

### Post by exploder on 2009-08-29
Same issue here. I tried adding to the bug report but there seems to be a problem with LaunchPad.

Edit: Finally got LaunchPad to save my "same here" comment.

---

### Post by Xgen on 2009-08-30
I am also getting seg faults with "gksu nautilus" and "sudo su". A temporary solution for me, until it is fixed, is to use "sudo dbus-launch nautilus".

---

### Post by nechus on 2009-08-31
> **Xgen said:**
> I am also getting seg faults with "gksu nautilus" and "sudo su". A temporary solution for me, until it is fixed, is to use "sudo dbus-launch nautilus".

You're right. It works! Thank you

---

