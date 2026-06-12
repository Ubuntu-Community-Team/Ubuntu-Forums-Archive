---
title: "Can't get cnet to install. Help would be brilliant."
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by zachwlewis on 2008-03-18
I've been trying to get [cnet]("http://www.csse.uwa.edu.au/cnet3") running on 7.10, but I've been having piss luck. I think I get all the paths set up correctly and stuff, but then I run make and I get a bunch of "conversion to int of different size" errors (although the author says his code works fine and it compiles and runs on OSX at school).

If anyone could take the time and let me know exactly how my settings should be set up, I'd greatly appreciate it.

I've installed Tcl8.4 and Tk8.4 and their dev packages using Synaptic, so I assume they're in the default locations.

Many thanks! :)

---

### Post by zachwlewis on 2008-03-23
Could anyone help me? I've got the paths set up correctly (I believe), but when I compile I get the following errors:

```
gcc -std=c99 -pedantic -Wall -Werror -O -fPIC -I/usr/include/libelf -I/usr/include/tcl8.4 -c compile.c
cc1: warnings being treated as errors
In file included from compile.c:35:
compile/linux.c: In function &#8216;data_segments&#8217;:
compile/linux.c:203: warning: cast from pointer to integer of different size
compile/linux.c:209: warning: cast to pointer from integer of different size
compile/linux.c:219: warning: cast to pointer from integer of different size
make[2]: *** [compile.o] Error 1
make[2]: Leaving directory `/home/zachwlewis/Desktop/cnet-3.0.19/src'
make[1]: *** [it] Error 2
make[1]: Leaving directory `/home/zachwlewis/Desktop/cnet-3.0.19/src'
make: *** [it] Error 2
```

I'm not sure if I've installed a 64-bit version of Ubuntu, but I know I have a 64-bit processor. Could that affect the int size of my machine?

---

