---
title: "aticonfig fails core dump gutsy"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by robaldred on 2007-11-26
This is my first ever desktop linux installation and now having much fun.
I'm very much a windows user, couple of mates at work have ubuntu and swear by it, so i thought i'd take a look.

I can't for the life of me get my graphics driver installed, I have an ATI X800 Pro
I've lost count the number of forums and blog posts I've read, a lot of people seem to have an issue with ATI cards, anyway, 

Most people says run: sudo aticonfig --initial
Well, I can't even get past that successfully.

I have a fresh 7.10 install... i get the following:
```

rob@rob-desktop:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf8a79f3 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d9392b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d3c050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 2142854    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 2142854    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7d03000-b7d0d000 r-xp 00000000 08:01 719555     /lib/libgcc_s.so.1
b7d0d000-b7d0e000 rw-p 0000a000 08:01 719555     /lib/libgcc_s.so.1
b7d18000-b7d19000 rw-p b7d18000 00:00 0 
b7d19000-b7d1b000 r-xp 00000000 08:01 753166     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d1b000-b7d1d000 rw-p 00001000 08:01 753166     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d1d000-b7d1e000 rw-p b7d1d000 00:00 0 
b7d1e000-b7d22000 r-xp 00000000 08:01 2143443    /usr/lib/libXdmcp.so.6.0.0
b7d22000-b7d23000 rw-p 00003000 08:01 2143443    /usr/lib/libXdmcp.so.6.0.0
b7d23000-b7d25000 r-xp 00000000 08:01 2143432    /usr/lib/libXau.so.6.0.0
b7d25000-b7d26000 rw-p 00001000 08:01 2143432    /usr/lib/libXau.so.6.0.0
b7d26000-b7e6a000 r-xp 00000000 08:01 753163     /lib/tls/i686/cmov/libc-2.6.1.so
b7e6a000-b7e6b000 r--p 00143000 08:01 753163     /lib/tls/i686/cmov/libc-2.6.1.so
b7e6b000-b7e6d000 rw-p 00144000 08:01 753163     /lib/tls/i686/cmov/libc-2.6.1.so
b7e6d000-b7e70000 rw-p b7e6d000 00:00 0 
b7e70000-b7e93000 r-xp 00000000 08:01 753167     /lib/tls/i686/cmov/libm-2.6.1.so
b7e93000-b7e95000 rw-p 00023000 08:01 753167     /lib/tls/i686/cmov/libm-2.6.1.so
b7e95000-b7f82000 r-xp 00000000 08:01 2143426    /usr/lib/libX11.so.6.2.0
b7f82000-b7f86000 rw-p 000ed000 08:01 2143426    /usr/lib/libX11.so.6.2.0
b7f86000-b7f93000 r-xp 00000000 08:01 2143447    /usr/lib/libXext.so.6.4.0
b7f93000-b7f94000 rw-p 0000d000 08:01 2143447    /usr/lib/libXext.so.6.4.0
b7f94000-b7f95000 rw-p b7f94000 00:00 0 
b7f95000-b7f9c000 r-xp 00000000 08:01 2143469    /usr/lib/libXrender.so.1.3.0
b7f9c000-b7f9d000 rw-p 00006000 08:01 2143469    /usr/lib/libXrender.so.1.3.0
b7f9d000-b7fa2000 r-xp 00000000 08:01 2143467    /usr/lib/libXrandr.so.2.1.0
b7fa2000-b7fa3000 rw-p 00005000 08:01 2143467    /usr/lib/libXrandr.so.2.1.0
b7fac000-b7faf000 rw-p b7fac000 00:00 0 
b7faf000-b7fc9000 r-xp 00000000 08:01 719709     /lib/ld-2.6.1.so
b7fc9000-b7fcb000 rw-p 00019000 08:01 719709     /lib/ld-2.6.1.so
bf893000-bf8a9000 rw-p bf893000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```
I can't use this how it is because the whole interface is laggy, even typing is lagged.


Thanks

Rob

---

### Post by angryarse on 2008-01-22
I sure wish someone would have answered you, cause I have same problem, WTF? ATI is such a problem w/ linux oh well, guess back to windows

---

### Post by adrian.agps on 2008-02-01
HI 
I am running Linux 2.6.20-16-realtime and have just installed a Radon Powercolor 9550.
I installed the Proprietary drivers without success so then installed the recommended
open source drivers. 
All is up and running but I am trying to get fglrx running and am following the help.ubuntu.com/community/BinaryDriverHowto/ATI.

When I get to the sudo aticonfig --overlay-type=Xv I get the same problem described above.

Thanks for any pointers

Adrian

---

### Post by sjrixon on 2008-02-02
Yes! I had the same issues. I had to set it all up with the basic driver and then manually add the fglrx entries to get it working..

Go through the setup for X. If you are really screwed then run this 'sudo dpkg-reconfigure xserver-xorg' which will get you back to a working config.

Backup (make a copy) of your working xorg.conf at this point so you can go back

Then add these lines to the end of xorg.conf

Section "Extetension"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Then find the 'ati' module entry and change it to 'fglrx' restart X and you should be working...

---

