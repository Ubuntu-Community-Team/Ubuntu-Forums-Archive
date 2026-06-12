---
title: "Upgrade to 12.04LTS Lost Ncurses Lib"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by FlaHAM on 2012-10-07
I upgraded my Servers from 10.04LTS to 12.04LTS as expected several things broke/changed. So far I have been able to fix the issues.

This last one has me stumped.
I am attempting to compile the FBB BBS source from [http://f6bvp.free.fr/logiciels/BBS-f6fbb/xd705c09-src.tar.bz2]("http://f6bvp.free.fr/logiciels/BBS-f6fbb/xd705c09-src.tar.bz2")

The same source compiles w/o a whimper under 10.04LTS.
When I attempt to compile I get 
```
root@Riverview:/usr/local/src/ax25/fbbsrc.705c9/src# make
gcc -Wall -O2 -Wstrict-prototypes -funsigned-char  -D__LINUX__ -DPROTOTYPES -I../include -fstack-check -DUSE_NCURSES -o xfbbC -lncurses xfbbC.o md5c.o terminal.o
terminal.o: In function `writeincom.isra.0.constprop.1':
terminal.c:(.text+0x59): undefined reference to `waddch'
terminal.c:(.text+0x9d): undefined reference to `waddch'
terminal.c:(.text+0xab): undefined reference to `acs_map'
terminal.c:(.text+0xb7): undefined reference to `waddch'
terminal.c:(.text+0xc3): undefined reference to `acs_map'
terminal.c:(.text+0xcf): undefined reference to `waddch'
     And More
collect2: ld returned 1 exit status
make: *** [xfbbC] Error 1


```

I've traced and symlinked to no avail.
The work around - compile w/o curses support - works to a point, but is unsatisfactory.

Any help will be appreciated.

---

