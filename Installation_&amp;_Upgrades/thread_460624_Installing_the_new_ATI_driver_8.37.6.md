---
title: "Installing the new ATI driver 8.37.6"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by qwicfingers on 2007-05-31
I installed the new ATI driver everything went fine followed the directions at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) but the sudo aticonfig --initial failed 

Anyone have a clue? Thanks.


> 
~/Desktop$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfceba38 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d8ef5b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7d39ebc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:01 10707076   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:01 10707076   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7cfc000-b7d07000 r-xp 00000000 03:01 9388046    /lib/libgcc_s.so.1
b7d07000-b7d08000 rw-p 0000a000 03:01 9388046    /lib/libgcc_s.so.1
b7d16000-b7d17000 rw-p b7d16000 00:00 0 
b7d17000-b7d19000 r-xp 00000000 03:01 9388188    /lib/tls/i686/cmov/libdl-2.5.so
b7d19000-b7d1b000 rw-p 00001000 03:01 9388188    /lib/tls/i686/cmov/libdl-2.5.so
b7d1b000-b7d1c000 rw-p b7d1b000 00:00 0 
b7d1c000-b7d20000 r-xp 00000000 03:01 10703534   /usr/lib/libXdmcp.so.6.0.0
b7d20000-b7d21000 rw-p 00003000 03:01 10703534   /usr/lib/libXdmcp.so.6.0.0
b7d21000-b7d23000 r-xp 00000000 03:01 10703532   /usr/lib/libXau.so.6.0.0
b7d23000-b7d24000 rw-p 00001000 03:01 10703532   /usr/lib/libXau.so.6.0.0
b7d24000-b7e5f000 r-xp 00000000 03:01 9388184    /lib/tls/i686/cmov/libc-2.5.so
b7e5f000-b7e60000 r--p 0013b000 03:01 9388184    /lib/tls/i686/cmov/libc-2.5.so
b7e60000-b7e62000 rw-p 0013c000 03:01 9388184    /lib/tls/i686/cmov/libc-2.5.so
b7e62000-b7e65000 rw-p b7e62000 00:00 0 
b7e65000-b7e8a000 r-xp 00000000 03:01 9388189    /lib/tls/i686/cmov/libm-2.5.so
b7e8a000-b7e8c000 rw-p 00024000 03:01 9388189    /lib/tls/i686/cmov/libm-2.5.so
b7e8c000-b7f79000 r-xp 00000000 03:01 10703536   /usr/lib/libX11.so.6.2.0
b7f79000-b7f7d000 rw-p 000ed000 03:01 10703536   /usr/lib/libX11.so.6.2.0
b7f7d000-b7f8a000 r-xp 00000000 03:01 10703573   /usr/lib/libXext.so.6.4.0
b7f8a000-b7f8b000 rw-p 0000d000 03:01 10703573   /usr/lib/libXext.so.6.4.0
b7f8b000-b7f8c000 rw-p b7f8b000 00:00 0 
b7f8c000-b7f93000 r-xp 00000000 03:01 10703538   /usr/lib/libXrender.so.1.3.0
b7f93000-b7f94000 rw-p 00006000 03:01 10703538   /usr/lib/libXrender.so.1.3.0
b7f94000-b7f99000 r-xp 00000000 03:01 10703579   /usr/lib/libXrandr.so.2.1.0
b7f99000-b7f9a000 rw-p 00005000 03:01 10703579   /usr/lib/libXrandr.so.2.1.0
b7fa7000-b7faa000 rw-p b7fa7000 00:00 0 
b7faa000-b7fc3000 r-xp 00000000 03:01 9388047    /lib/ld-2.5.so
b7fc3000-b7fc5000 rw-p 00019000 03:01 9388047    /lib/ld-2.5.so
bfcd7000-bfced000 rw-p bfcd7000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


---

