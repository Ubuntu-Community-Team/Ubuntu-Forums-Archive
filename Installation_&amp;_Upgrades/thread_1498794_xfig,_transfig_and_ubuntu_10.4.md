---
title: "xfig, transfig and ubuntu 10.4"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by Jon Saenz on 2010-06-01
Hi, all.

I have recently installed ubuntu 10.4 desktop and I am unable to use transfig. After creating an xfig file as usual (I see the graphics in the X window), when I try to convert it to a PDF file, I get an error code from xfig. If I try to get the pdf file by means of a command, like this:
fig2dev -L pdf -p p eigenvalues-versus-L.fig > eigenvalues-versus-L.pdf

The output is:

fig2dev -L pdf -p p eigenvalues-versus-L.fig > eigenvalues-versus-L.pdf
GPL Ghostscript 8.71: Unrecoverable error, exit code 1
Error in ghostcript command
command was: gs -q -dNOPAUSE -sAutoRotatePages=None -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -sDEVICE=pdfwrite -dPDFSETTINGS=/prepress -sOutputFile=- - -c quit
*** glibc detected *** fig2dev: double free or corruption (!prev): 0x092d3030 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xb75fa591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0xb75fbde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xb75feecd]
/lib/tls/i686/cmov/libc.so.6(fclose+0x14a)[0xb75eaaaa]
fig2dev[0x804ba8c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb75a5bd6]
fig2dev[0x8049d71]
======= Memory map: ========
08048000-080af000 r-xp 00000000 08:01 132946     /usr/bin/fig2dev
080af000-080b0000 r--p 00066000 08:01 132946     /usr/bin/fig2dev
080b0000-080b4000 rw-p 00067000 08:01 132946     /usr/bin/fig2dev
080b4000-080c7000 rw-p 00000000 00:00 0 
092d3000-092f4000 rw-p 00000000 00:00 0          [heap]
b7400000-b7421000 rw-p 00000000 00:00 0 
b7421000-b7500000 ---p 00000000 00:00 0 
b7510000-b752d000 r-xp 00000000 08:01 1835100    /lib/libgcc_s.so.1
b752d000-b752e000 r--p 0001c000 08:01 1835100    /lib/libgcc_s.so.1
b752e000-b752f000 rw-p 0001d000 08:01 1835100    /lib/libgcc_s.so.1
b752f000-b7539000 r-xp 00000000 08:01 1835132    /lib/tls/i686/cmov/libnss_files-2.11.1.so
b7539000-b753a000 r--p 00009000 08:01 1835132    /lib/tls/i686/cmov/libnss_files-2.11.1.so
b753a000-b753b000 rw-p 0000a000 08:01 1835132    /lib/tls/i686/cmov/libnss_files-2.11.1.so
b753b000-b754e000 r-xp 00000000 08:01 1835126    /lib/tls/i686/cmov/libnsl-2.11.1.so
b754e000-b754f000 r--p 00012000 08:01 1835126    /lib/tls/i686/cmov/libnsl-2.11.1.so
b754f000-b7550000 rw-p 00013000 08:01 1835126    /lib/tls/i686/cmov/libnsl-2.11.1.so
b7550000-b7552000 rw-p 00000000 00:00 0 
b7565000-b7566000 rw-p 00000000 00:00 0 
b7566000-b756a000 r-xp 00000000 08:01 134266     /usr/lib/libXdmcp.so.6.0.0
b756a000-b756b000 r--p 00003000 08:01 134266     /usr/lib/libXdmcp.so.6.0.0
b756b000-b756c000 rw-p 00004000 08:01 134266     /usr/lib/libXdmcp.so.6.0.0
b756c000-b756e000 r-xp 00000000 08:01 134255     /usr/lib/libXau.so.6.0.0
b756e000-b756f000 r--p 00001000 08:01 134255     /usr/lib/libXau.so.6.0.0
b756f000-b7570000 rw-p 00002000 08:01 134255     /usr/lib/libXau.so.6.0.0
b7570000-b7572000 r-xp 00000000 08:01 1835080    /lib/tls/i686/cmov/libdl-2.11.1.so
b7572000-b7573000 r--p 00001000 08:01 1835080    /lib/tls/i686/cmov/libdl-2.11.1.so
b7573000-b7574000 rw-p 00002000 08:01 1835080    /lib/tls/i686/cmov/libdl-2.11.1.so
b7574000-b7575000 rw-p 00000000 00:00 0 
b7575000-b758d000 r-xp 00000000 08:01 135262     /usr/lib/libxcb.so.1.1.0
b758d000-b758e000 r--p 00017000 08:01 135262     /usr/lib/libxcb.so.1.1.0
b758e000-b758f000 rw-p 00018000 08:01 135262     /usr/lib/libxcb.so.1.1.0
b758f000-b76e2000 r-xp 00000000 08:01 1835066    /lib/tls/i686/cmov/libc-2.11.1.so
b76e2000-b76e3000 ---p 00153000 08:01 1835066    /lib/tls/i686/cmov/libc-2.11.1.so
b76e3000-b76e5000 r--p 00153000 08:01 1835066    /lib/tls/i686/cmov/libc-2.11.1.so
b76e5000-b76e6000 rw-p 00155000 08:01 1835066    /lib/tls/i686/cmov/libc-2.11.1.so
b76e6000-b76e9000 rw-p 00000000 00:00 0 
b76e9000-b770d000 r-xp 00000000 08:01 1835115    /lib/tls/i686/cmov/libm-2.11.1.so
b770d000-b770e000 r--p 00023000 08:01 1835115    /lib/tls/i686/cmov/libm-2.11.1.so
b770e000-b770f000 rw-p 00024000 08:01 1835115    /lib/tls/i686/cmov/libm-2.11.1.so
b770f000-b7828000 r-xp 00000000 08:01 134251     /usr/lib/libX11.so.6.3.0
b7828000-b7829000 r--p 00118000 08:01 134251     /usr/lib/libX11.so.6.3.0
b7829000-b782b000 rw-p 00119000 08:01 134251     /usr/lib/libX11.so.6.3.0
b782b000-b782c000 rw-p 00000000 00:00 0 
b782c000-b783b000 r-xp 00000000 08:01 134286     /usr/lib/libXpm.so.4.11.0
b783b000-b783c000 r--p 0000e000 08:01 134286     /usr/lib/libXpm.so.4.11.0
b783c000-b783d000 rw-p 0000f000 08:01 134286     /usr/lib/libXpm.so.4.11.0
b783d000-b783e000 rw-p 00000000 00:00 0 
b783e000-b7851000 r-xp 00000000 08:01 1835215    /lib/libz.so.1.2.3.3
b7851000-b7852000 r--p 00012000 08:01 1835215    /lib/libz.so.1.2.3.3
b7852000-b7853000 rw-p 00013000 08:01 1835215    /lib/libz.so.1.2.3.3
b7853000-b7876000 r-xp 00000000 08:01 1835170    /lib/libpng12.so.0.42.0
b7876000-b7877000 r--p 00022000 08:01 1835170    /lib/libpng12.so.0.42.0
b7877000-b7878000 rw-p 00023000 08:01 1835170    /lib/libpng12.so.0.42.0
b7878000-b7880000 r-xp 00000000 08:01 1835142    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b7880000-b7881000 r--p 00007000 08:01 1835142    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b7881000-b7882000 rw-p 00008000 08:01 1835142    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b7882000-b7888000 r-xp 00000000 08:01 1835128    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b7888000-b7889000 r--p 00006000 08:01 1835128    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b7889000-b788a000 rw-p 00007000 08:01 1835128    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b788b000-b788d000 rw-p 00000000 00:00 0 
b788d000-b788e000 r-xp 00000000 00:00 0          [vdso]
b788e000-b78a9000 r-xp 00000000 08:01 1839226    /lib/ld-2.11.1.so
b78a9000-b78aa000 r--p 0001a000 08:01 1839226    /lib/ld-2.11.1.so
b78aa000-b78ab000 rw-p 0001b000 08:01 1839226    /lib/ld-2.11.1.so
bfc19000-bfc2e000 rw-p 00000000 00:00 0          [stack]
Aborted


I have removed xfig, xfig-libs and transfig and installed them from source, but I have had no success. Any hint/idea?

Thanks in advance.

---

