---
title: "Conky quitting"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by RichardCain on 2011-07-25
I'm running 11.04 with Unity (which, for the record is generally fantastic), but have a problem with Conky.
Conky starts up and works OK, but then eventually quits.  Running in a terminal, I get the following as it starts:

<code>richard@richard-laptop:~$ conky
Conky: desktop window (10000b8) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer</code>

and as it quits:

<code>*** longjmp causes uninitialized stack frame ***: conky terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x50)[0x713df0]
/lib/i386-linux-gnu/libc.so.6(+0xe5d5a)[0x713d5a]
/usr/lib/libcurl-gnutls.so.4(+0x8b08)[0x233b08]
[0x556400]
conky[0x807bf94]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0x644e37]
conky[0x804e6b1]
======= Memory map: ========
00110000-00226000 r-xp 00000000 08:06 13716      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00226000-00227000 ---p 00116000 08:06 13716      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00227000-00228000 r--p 00116000 08:06 13716      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00228000-0022a000 rw-p 00117000 08:06 13716      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
0022a000-0022b000 rw-p 00000000 00:00 0 
0022b000-00277000 r-xp 00000000 08:06 129        /usr/lib/libcurl-gnutls.so.4.2.0
00277000-00278000 r--p 0004c000 08:06 129        /usr/lib/libcurl-gnutls.so.4.2.0
00278000-00279000 rw-p 0004d000 08:06 129        /usr/lib/libcurl-gnutls.so.4.2.0
00279000-0027b000 r-xp 00000000 08:06 129120     /lib/i386-linux-gnu/libdl-2.13.so
0027b000-0027c000 r--p 00001000 08:06 129120     /lib/i386-linux-gnu/libdl-2.13.so
0027c000-0027d000 rw-p 00002000 08:06 129120     /lib/i386-linux-gnu/libdl-2.13.so
0027d000-0027f000 r-xp 00000000 08:06 13720      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
0027f000-00280000 r--p 00001000 08:06 13720      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00280000-00281000 rw-p 00002000 08:06 13720      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00281000-00283000 r-xp 00000000 08:06 129114     /lib/i386-linux-gnu/libcom_err.so.2.1
00283000-00284000 r--p 00001000 08:06 129114     /lib/i386-linux-gnu/libcom_err.so.2.1
00284000-00285000 rw-p 00002000 08:06 129114     /lib/i386-linux-gnu/libcom_err.so.2.1
00286000-002a2000 r-xp 00000000 08:06 129096     /lib/i386-linux-gnu/ld-2.13.so
002a2000-002a3000 r--p 0001b000 08:06 129096     /lib/i386-linux-gnu/ld-2.13.so
002a3000-002a4000 rw-p 0001c000 08:06 129096     /lib/i386-linux-gnu/ld-2.13.so
002a4000-002ed000 r-xp 00000000 08:06 4744       /usr/lib/libImlib2.so.1.4.2
002ed000-002ee000 r--p 00048000 08:06 4744       /usr/lib/libImlib2.so.1.4.2
002ee000-002ef000 rw-p 00049000 08:06 4744       /usr/lib/libImlib2.so.1.4.2
002ef000-00303000 rw-p 00000000 00:00 0 
00303000-003d8000 r-xp 00000000 08:06 129142     /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
003d8000-003d9000 r--p 000d4000 08:06 129142     /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
003d9000-003da000 rw-p 000d5000 08:06 129142     /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
003da000-003f1000 r-xp 00000000 08:06 13968      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
003f1000-003f2000 r--p 00016000 08:06 13968      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
003f2000-003f3000 rw-p 00017000 08:06 13968      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
003f3000-00418000 r-xp 00000000 08:06 9830       /usr/lib/liblua5.1.so.0.0.0
00418000-00419000 r--p 00024000 08:06 9830       /usr/lib/liblua5.1.so.0.0.0
00419000-0041a000 rw-p 00025000 08:06 9830       /usr/lib/liblua5.1.so.0.0.0
0041a000-00422000 r-xp 00000000 08:06 13764      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00422000-00423000 r--p 00007000 08:06 13764      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00423000-00424000 rw-p 00008000 08:06 13764      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00424000-0042f000 r-xp 00000000 08:06 9805       /usr/lib/liblber-2.4.so.2.5.6
0042f000-00430000 r--p 0000a000 08:06 9805       /usr/lib/liblber-2.4.so.2.5.6
00430000-00431000 rw-p 0000b000 08:06 9805       /usr/lib/liblber-2.4.so.2.5.6
00433000-0043a000 r-xp 00000000 08:06 128332     /lib/libiw.so.30
0043a000-0043b000 r--p 00006000 08:06 128332     /lib/libiw.so.30
0043b000-0043c000 rw-p 00007000 08:06 128332     /lib/libiw.so.30
0043c000-00503000 r-xp 00000000 08:06 9079       /usr/lib/libasound.so.2.0.0
00503000-00507000 r--p 000c6000 08:06 9079       /usr/lib/libasound.so.2.0.0
00507000-00508000 rw-p 000ca000 08:06 9079       /usr/lib/libasound.so.2.0.0
00508000-00535000 r-xp 00000000 08:06 13828      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00535000-00536000 r--p 0002c000 08:06 13828      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00536000-00537000 rw-p 0002d000 08:06 13828      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00537000-0053b000 r-xp 00000000 08:06 13736      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0053b000-0053c000 r--p 00003000 08:06 13736      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0053c000-0053d000 rw-p 00004000 08:06 13736      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0053d000-0054e000 r-xp 00000000 08:06 129179     /lib/i386-linux-gnu/libresolv-2.13.so
0054e000-0054f000 r--p 00010000 08:06 129179     /lib/i386-linux-gnu/libresolv-2.13.so
0054f000-00550000 rw-p 00011000 08:06 129179     /lib/i386-linux-gnu/libresolv-2.13.so
00550000-00552000 rw-p 00000000 00:00 0 
00552000-00554000 r-xp 00000000 08:06 13964      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00554000-00555000 r--p 00001000 08:06 13964      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00555000-00556000 rw-p 00002000 08:06 13964      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00556000-00557000 r-xp 00000000 00:00 0          [vdso]
00557000-005d8000 r-xp 00000000 08:06 13833      /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
005d8000-005dc000 r--p 00080000 08:06 13833      /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
005dc000-005dd000 rw-p 00084000 08:06 13833      /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
005dd000-005f2000 r-xp 00000000 08:06 10120      /usr/lib/libsasl2.so.2.0.23
005f2000-005f3000 r--p 00015000 08:06 10120      /usr/lib/libsasl2.so.2.0.23
005f3000-005f4000 rw-p 00016000 08:06 10120      /usr/lib/libsasl2.so.2.0.23
005f6000-0062a000 r-xp 00000000 08:06 128335     /lib/libncurses.so.5.7
0062a000-0062b000 ---p 00034000 08:06 128335     /lib/libncurses.so.5.7
0062b000-0062d000 r--p 00034000 08:06 128335     /lib/libncurses.so.5.7
0062d000-0062e000 rw-p 00036000 08:06 128335     /lib/libncurses.so.5.7
0062e000-00788000 r-xp 00000000 08:06 129109     /lib/i386-linux-gnu/libc-2.13.so
00788000-00789000 ---p 0015a000 08:06 129109     /lib/i386-linux-gnu/libc-2.13.so
00789000-0078b000 r--p 0015a000 08:06 129109     /lib/i386-linux-gnu/libc-2.13.so
0078b000-0078c000 rw-p 0015c000 08:06 129109     /lib/i386-linux-gnu/libc-2.13.so
0078c000-0078f000 rw-p 00000000 00:00 0 
0078f000-007bd000 r-xp 00000000 08:06 13868      /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
007bd000-007be000 r--p 0002d000 08:06 13868      /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
007be000-007bf000 rw-p 0002e000 08:06 13868      /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2Aborted</code>

Any suggestions?

---

### Post by cfjrocha on 2012-03-31
I found this tip ...
[http://stackoverflow.com/questions/9191668/error-longjmp-causes-uninitialized-stack-frame](http://stackoverflow.com/questions/9191668/error-longjmp-causes-uninitialized-stack-frame)
[http://linux.die.net/man/3/curl_easy_setopt](http://linux.die.net/man/3/curl_easy_setopt)

---

### Post by RichardCain on 2012-04-06
Hi cfjrocha,

Thanks for your effort but, to be honest, I'd completely forgotten about this!  I've long-since given up on Unity and returned to the one true desktop (for me anyway) - Xfce.
No more Conky problems :)

---

