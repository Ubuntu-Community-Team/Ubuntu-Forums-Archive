---
title: "Help me! wifi not detect after update kernel to 3.03"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by hidayahweb on 2011-08-19
sorry im from indonesian (newbie english+ubuntu)

im using ubuntu ultimate 2.9 (maverick)
initially bluetooth not functioning
after kernel update to 3.03:
-bluetooth detected
-sound and vga nicely installed
but
wirelless driver is not installed.
when there is a kernel update folder called hybrid-portsrc who it was told to install the driver manually. ane then install the appropriate readme. during the make actually result like this. there who can help?

> dhonz@dona:~/hybrid-portsrc_x86_32-v5_100_82_38$ ls
built-in.o  lib  Makefile  src
dhonz@dona:~/hybrid-portsrc_x86_32-v5_100_82_38$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-3.0.3'
  CC [M]  /home/dhonz/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.o
/home/dhonz/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/dhonz/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.c:485: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/home/dhonz/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/dhonz/hybrid-portsrc_x86_32-v5_100_82_38] Error 2
make[1]: Leaving directory `/usr/src/linux-3.0.3'
make: *** [all] Error 2
dhonz@dona:~/hybrid-portsrc_x86_32-v5_100_82_38$ 


using root user:
> root@dona:~/hybrid_wl# make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-3.0.3'
  CC [M]  /root/hybrid_wl/src/wl/sys/wl_linux.o
/root/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;_wl_set_multicast_list&#8217;:
/root/hybrid_wl/src/wl/sys/wl_linux.c:1435: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_list&#8217;
/root/hybrid_wl/src/wl/sys/wl_linux.c:1435: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/root/hybrid_wl/src/wl/sys/wl_linux.c:1436: error: dereferencing pointer to incomplete type
/root/hybrid_wl/src/wl/sys/wl_linux.c:1442: error: dereferencing pointer to incomplete type
make[2]: *** [/root/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/root/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-3.0.3'
make: *** [all] Error 2
root@dona:~/hybrid_wl#

once again sorry if my language is not appropriate

---

### Post by kyletstrand on 2011-08-21
Just a blind guess without looking too closely at it, but try this instead and post results:

Before doing your make command, type
```
./configure
```
Now after that do 
```
make
sudo make install
```

like I said, I don't know if it'll work, but give it a try and post results.

---

