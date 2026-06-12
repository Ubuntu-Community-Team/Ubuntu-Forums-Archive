---
title: "ATI breaks at auto config"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Spreggo on 2007-04-21
The following happens when I hit the final step of the ati driver install. I am using an Radeon x1900xt. Anyone know what to do at this point? Thanks.

> spreggo@The-Ugly-Bream:~/Desktop$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfea7a0a ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d29f5b]
aticonfig[0x805bff7]
aticonfig[0x805c2a5]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7cd4ebc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:07 687518     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:07 687518     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c9b000-b7ca6000 r-xp 00000000 08:07 2665440    /lib/libgcc_s.so.1
b7ca6000-b7ca7000 rw-p 0000a000 08:07 2665440    /lib/libgcc_s.so.1
b7cb1000-b7cb2000 rw-p b7cb1000 00:00 0 
b7cb2000-b7cb4000 r-xp 00000000 08:07 2699368    /lib/tls/i686/cmov/libdl-2.5.so
b7cb4000-b7cb6000 rw-p 00001000 08:07 2699368    /lib/tls/i686/cmov/libdl-2.5.so
b7cb6000-b7cb7000 rw-p b7cb6000 00:00 0 
b7cb7000-b7cbb000 r-xp 00000000 08:07 688069     /usr/lib/libXdmcp.so.6.0.0
b7cbb000-b7cbc000 rw-p 00003000 08:07 688069     /usr/lib/libXdmcp.so.6.0.0
b7cbc000-b7cbe000 r-xp 00000000 08:07 688058     /usr/lib/libXau.so.6.0.0
b7cbe000-b7cbf000 rw-p 00001000 08:07 688058     /usr/lib/libXau.so.6.0.0
b7cbf000-b7dfa000 r-xp 00000000 08:07 2699362    /lib/tls/i686/cmov/libc-2.5.so
b7dfa000-b7dfb000 r--p 0013b000 08:07 2699362    /lib/tls/i686/cmov/libc-2.5.so
b7dfb000-b7dfd000 rw-p 0013c000 08:07 2699362    /lib/tls/i686/cmov/libc-2.5.so
b7dfd000-b7e00000 rw-p b7dfd000 00:00 0 
b7e00000-b7e25000 r-xp 00000000 08:07 2699370    /lib/tls/i686/cmov/libm-2.5.so
b7e25000-b7e27000 rw-p 00024000 08:07 2699370    /lib/tls/i686/cmov/libm-2.5.so
b7e27000-b7f14000 r-xp 00000000 08:07 688052     /usr/lib/libX11.so.6.2.0
b7f14000-b7f18000 rw-p 000ed000 08:07 688052     /usr/lib/libX11.so.6.2.0
b7f18000-b7f25000 r-xp 00000000 08:07 688073     /usr/lib/libXext.so.6.4.0
b7f25000-b7f26000 rw-p 0000d000 08:07 688073     /usr/lib/libXext.so.6.4.0
b7f26000-b7f27000 rw-p b7f26000 00:00 0 
b7f27000-b7f2e000 r-xp 00000000 08:07 688095     /usr/lib/libXrender.so.1.3.0
b7f2e000-b7f2f000 rw-p 00006000 08:07 688095     /usr/lib/libXrender.so.1.3.0
b7f2f000-b7f34000 r-xp 00000000 08:07 688093     /usr/lib/libXrandr.so.2.1.0
b7f34000-b7f35000 rw-p 00005000 08:07 688093     /usr/lib/libXrandr.so.2.1.0
b7f3e000-b7f41000 rw-p b7f3e000 00:00 0 
b7f41000-b7f5a000 r-xp 00000000 08:07 2665397    /lib/ld-2.5.so
b7f5a000-b7f5c000 rw-p 00019000 08:07 2665397    /lib/ld-2.5.so
bfe93000-bfea8000 rw-p bfe93000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


---

### Post by FIREcracker on 2007-05-10
ehy man, have you found a solution to it?
M@

---

### Post by FIREcracker on 2007-05-10
another entry, but now with the solution...
[http://www.rage3d.com/board/showthread.php?t=33889029](http://www.rage3d.com/board/showthread.php?t=33889029)
and the script for the installation
[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)
M@

---

