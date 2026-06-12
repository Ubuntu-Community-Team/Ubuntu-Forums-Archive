---
title: "conky has started crashing frequently"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David Tomic on 2008-09-02
For perhaps the last week or so, I've noticed that conky has begun crashing really frequently.

I'm just wondering if anyone else is having troubles as well?

Here's the output that I get from a console window [apologies for the length]

> david@einstein:~$ conky
Conky: forked to background, pid is 11428
david@einstein:~$ 
Conky: desktop window (1a000b4) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x3600001)
Conky: drawing to double buffer
*** buffer overflow detected ***: conky terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f0cfde2e7d7]
/lib/libc.so.6[0x7f0cfde2c6a0]
/lib/libc.so.6[0x7f0cfde2ba39]
/lib/libc.so.6(_IO_default_xsputn+0x96)[0x7f0cfdda71c6]
/lib/libc.so.6(_IO_vfprintf+0x63b)[0x7f0cfdd76dbb]
/lib/libc.so.6(__vsprintf_chk+0x9d)[0x7f0cfde2badd]
/lib/libc.so.6(__sprintf_chk+0x80)[0x7f0cfde2ba20]
conky[0x421afd]
conky[0x406589]
conky[0x419212]
conky[0x41a87d]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f0cfdd4d466]
conky[0x405ca9]
======= Memory map: ========
00400000-00437000 r-xp 00000000 08:01 4326674                            /usr/bin/conky
00636000-00637000 r--p 00036000 08:01 4326674                            /usr/bin/conky
00637000-00638000 rw-p 00037000 08:01 4326674                            /usr/bin/conky
00638000-00646000 rw-p 00638000 00:00 0 
0193d000-019c1000 rw-p 0193d000 00:00 0                                  [heap]
7f0cfb4eb000-7f0cfb501000 r-xp 00000000 08:01 9715815                    /lib/libgcc_s.so.1
7f0cfb501000-7f0cfb700000 ---p 00016000 08:01 9715815                    /lib/libgcc_s.so.1
7f0cfb700000-7f0cfb701000 r--p 00015000 08:01 9715815                    /lib/libgcc_s.so.1
7f0cfb701000-7f0cfb702000 rw-p 00016000 08:01 9715815                    /lib/libgcc_s.so.1
7f0cfb702000-7f0cfb729000 r-xp 00000000 08:01 4327265                    /usr/lib/libexpat.so.1.5.2
7f0cfb729000-7f0cfb929000 ---p 00027000 08:01 4327265                    /usr/lib/libexpat.so.1.5.2
7f0cfb929000-7f0cfb92b000 r--p 00027000 08:01 4327265                    /usr/lib/libexpat.so.1.5.2
7f0cfb92b000-7f0cfb92c000 rw-p 00029000 08:01 4327265                    /usr/lib/libexpat.so.1.5.2
7f0cfb92c000-7f0cfb931000 r-xp 00000000 08:01 4325536                    /usr/lib/libXdmcp.so.6.0.0
7f0cfb931000-7f0cfbb30000 ---p 00005000 08:01 4325536                    /usr/lib/libXdmcp.so.6.0.0
7f0cfbb30000-7f0cfbb31000 rw-p 00004000 08:01 4325536                    /usr/lib/libXdmcp.so.6.0.0
7f0cfbb31000-7f0cfbb4b000 r-xp 00000000 08:01 9716256                    /lib/libselinux.so.1
7f0cfbb4b000-7f0cfbd4a000 ---p 0001a000 08:01 9716256                    /lib/libselinux.so.1
7f0cfbd4a000-7f0cfbd4b000 r--p 00019000 08:01 9716256                    /lib/libselinux.so.1
7f0cfbd4b000-7f0cfbd4c000 rw-p 0001a000 08:01 9716256                    /lib/libselinux.so.1
7f0cfbd4c000-7f0cfbd4d000 rw-p 7f0cfbd4c000 00:00 0 
7f0cfbd4d000-7f0cfbd75000 r-xp 00000000 08:01 9716181                    /lib/libpcre.so.3.12.1
7f0cfbd75000-7f0cfbf74000 ---p 00028000 08:01 9716181                    /lib/libpcre.so.3.12.1
7f0cfbf74000-7f0cfbf75000 r--p 00027000 08:01 9716181                    /lib/libpcre.so.3.12.1
7f0cfbf75000-7f0cfbf76000 rw-p 00028000 08:01 9716181                    /lib/libpcre.so.3.12.1
7f0cfbf76000-7f0cfbf7f000 r-xp 00000000 08:01 4327490                    /usr/lib/libXrender.so.1.3.0
7f0cfbf7f000-7f0cfc17e000 ---p 00009000 08:01 4327490                    /usr/lib/libXrender.so.1.3.0
7f0cfc17e000-7f0cfc17f000 r--p 00008000 08:01 4327490                    /usr/lib/libXrender.so.1.3.0
7f0cfc17f000-7f0cfc180000 rw-p 00009000 08:01 4327490                    /usr/lib/libXrender.so.1.3.0
7f0cfc180000-7f0cfc1fe000 r-xp 00000000 08:01 4325471                    /usr/lib/libfreetype.so.6.3.18
7f0cfc1fe000-7f0cfc3fe000 ---p 0007e000 08:01 4325471                    /usr/lib/libfreetype.so.6.3.18
7f0cfc3fe000-7f0cfc403000 r--p 0007e000 08:01 4325471                    /usr/lib/libfreetype.so.6.3.18
7f0cfc403000-7f0cfc404000 rw-p 00083000 08:01 4325471                    /usr/lib/libfreetype.so.6.3.18
7f0cfc404000-7f0cfc434000 r-xp 00000000 08:01 4325562                    /usr/lib/libfontconfig.so.1.3.0
7f0cfc434000-7f0cfc634000 ---p 00030000 08:01 4325562                    /usr/lib/libfontconfig.so.1.3.0
7f0cfc634000-7f0cfc635000 r--p 00030000 08:01 4325562                    /usr/lib/libfontconfig.so.1.3.0
7f0cfc635000-7f0cfc636000 rw-p 00031000 08:01 4325562                    /usr/lib/libfontconfig.so.1.3.0
7f0cfc636000-7f0cfc638000 r-xp 00000000 08:01 4325394                    /usr/lib/libXau.so.6.0.0
7f0cfc638000-7f0cfc837000 ---p 00002000 08:01 4325394                    /usr/lib/libXau.so.6.0.0
7f0cfc837000-7f0cfc838000 rw-p 00001000 08:01 4325394                    /usr/lib/libXau.so.6.0.0
7f0cfc838000-7f0cfc853000 r-xp 00000000 08:01 4325801                    /usr/lib/libxcb.so.1.0.0
7f0cfc853000-7f0cfca52000 ---p 0001b000 08:01 4325801                    /usr/lib/libxcb.so.1.0.0
7f0cfca52000-7f0cfca53000 r--p 0001a000 08:01 4325801                    /usr/lib/libxcb.so.1.0.0
7f0cfca53000-7f0cfca54000 rw-p 0001b000 08:01 4325801                    /usr/lib/libxcb.so.1.0.0
7f0cfca54000-7f0cfca55000 r-xp 00000000 08:01 4325815                    /usr/lib/libxcb-xlib.so.0.0.0
7f0cfca55000-7f0cfcc54000 ---p 00001000 08:01 4325815                    /usr/lib/libxcb-xlib.so.0.0.0
7f0cfcc54000-7f0cfcc55000 r--p 00000000 08:01 4325815                    /usr/lib/libxcb-xlib.so.0.0.0
7f0cfcc55000-7f0cfcc56000 rw-p 00001000 08:01 4325815                    /usr/lib/libxcb-xlib.so.0.0.0
7f0cfcc56000-7f0cfcc59000 r-xp 00000000 08:01 9715782                    /lib/libgpg-error.so.0.3.0
7f0cfcc59000-7f0cfce58000 ---p 00003000 08:01 9715782                    /lib/libgpg-error.so.0.3.0
7f0cfce58000-7f0cfce59000 rw-p 00002000 08:01 9715782                    /lib/libgpg-error.so.0.3.0
7f0cfce59000-7f0cfce5b000 r-xp 00000000 08:01 9715779                    /lib/libkeyutils-1.2.so
7f0cfce5b000-7f0cfd05a000 ---p 00002000 08:01 9715779                    /lib/libkeyutils-1.2.so
7f0cfd05a000-7f0cfd05c000 rw-p 00001000 08:01 9715779                    /lib/libkeyutils-1.2.so
7f0cfd05c000-7f0cfd063000 r-xp 00000000 08:01 4327113                    /usr/lib/libkrb5support.so.0.1
7f0cfd063000-7f0cfd262000 ---p 00007000 08:01 4327113                    /usr/lib/libkrb5support.so.0.1
7f0cfd262000-7f0cfd263000 r--p 00006000 08:01 4327113                    /usr/lib/libkrb5support.so.0.1
7f0cfd263000-7f0cfd264000 rw-p 00007000 08:01 4327113                    /usr/lib/libkrb5support.so.0.1
7f0cfd264000-7f0cfd276000 r-xp 00000000 08:01 9716318                    /lib/libresolv-2.8.90.so
7f0cfd276000-7f0cfd475000 ---p 00012000 08:01 9716318                    /lib/libresolv-2.8.90.so
7f0cfd475000-7f0cfd476000 r--p 00011000 08:01 9716318                    /lib/libresolv-2.8.90.so
7f0cfd476000-7f0cfd477000 rw-p 00012000 08:01 9716318                    /lib/libresolv-2.8.90.so
7f0cfd477000-7f0cfd479000 rw-p 7f0cfd477000 00:00 0 
7f0cfd479000-7f0cfd492000 r-xp 00000000 08:01 4327741                    /usr/lib/libsasl2.so.2.0.22
7f0cfd492000-7f0cfd691000 ---p 00019000 08:01 4327741                    /usr/lib/libsasl2.so.2.0.22
7f0cfd691000-7f0cfd692000 r--p 00018000 08:01 4327741                    /usr/lib/libsasl2.so.2.0.22
7f0cfd692000-7f0cfd693000 rw-p 00019000 08:01 4327741                    /usr/lib/libsasl2.so.2.0.22
7f0cfd693000-7f0cfd6a1000 r-xp 00000000 08:01 4326968                    /usr/lib/liblber-2.4.so.2.1.0
7f0cfd6a1000-7f0cfd8a0000 ---p 0000e000 08:01 4326968                    /usr/lib/liblber-2.4.so.2.1.0
7f0cfd8a0000-7f0cfd8a1000 r--p 0000d000 08:01 4326968                    /usr/lib/liblber-2.4.so.2.1.0
7f0cfd8a1000-7f0cfd8a2000 rw-p 0000e000 08:01 4326968                    /usr/lib/liblber-2.4.so.2.1.0
7f0cfd8a2000-7f0cfd921000 r-xp 00000000 08:01 4327213                    /usr/lib/libgnutls.so.13.9.1
7f0cfd921000-7f0cfdb21000 ---p 0007f000 08:01 4327213                    /usr/lib/libgnutls.so.13.9.1
7f0cfdb21000-7f0cfdb2a000 r--p 0007f000 08:01 4327213                    /usr/lib/libgnutls.so.13.9.1
7f0cfdb2a000-7f0cfdb2b000 rw-p 00088000 08:01 4327213                    /usr/lib/libgnutls.so.13.9.1
7f0cfdb2b000-7f0cfdb2d000 r-xp 00000000 08:01 9716186                    /lib/libdl-2.8.90.so
7f0cfdb2d000-7f0cfdd2d000 ---p 00002000 08:01 9716186                    /lib/libdl-2.8.90.so
7f0cfdd2d000-7f0cfdd2e000 r--p 00002000 08:01 9716186                    /lib/libdl-2.8.90.so
7f0cfdd2e000-7f0cfdd2f000 rw-p 00003000 08:01 9716186                    /lib/libdl-2.8.90.so
7f0cfdd2f000-7f0cfde98000 r-xp 00000000 08:01 9715900                    /lib/libc-2.8.90.so
7f0cfde98000-7f0cfe097000 ---p 00169000 08:01 9715900                    /lib/libc-2.8.90.so
7f0cfe097000-7f0cfe09b000 r--p 00168000 08:01 9715900                    /lib/libc-2.8.90.so
7f0cfe09b000-7f0cfe09c000 rw-p 0016c000 08:01 9715900                    /lib/libc-2.8.90.so
7f0cfe09c000-7f0cfe0a1000 rw-p 7f0cfe09c000 00:00 0 
7f0cfe0a1000-7f0cfe164000 r-xp 00000000 08:01 4328323

---

