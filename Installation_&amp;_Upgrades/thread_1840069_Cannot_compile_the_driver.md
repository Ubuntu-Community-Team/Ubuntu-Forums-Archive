---
title: "Cannot compile the driver"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by clowthu.ind on 2011-09-06
greetings guys, i need help to solve my compile problem
i cannot detect anything wireless since im upgrading kernel to 2.6.39.4
my wifi is broadcom BCM43225 802.11b/g/n

im trying to do the following
```

1. Download the Broadcom drivers: http://www.broadcom.com/support/802.11/linux_sta.php
2. Unpack and modify the ‘src/wl/sys/wl_linux.c‘:
Line 35 (after #include <linux/etherdevice.h>) add:

#include < linux/sched.h >

3. Compile the code with: make
4. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
5. Update dependencies: sudo depmod -a
6. Modify the blacklist to include the ‘b43&#8242; and ’ssb’ drivers /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)

The part above you probably have seen a few times while googling for the  answer. But there is a small problem, as you would have noticed, the  ‘ssb‘ driver cannot be blacklisted. It is included in the initrd as I  remember from the ubuntuforums. To solve this issue modify the  /etc/rc.local to include before the exit(0):

Code:

rmmod ssb
modprobe wl

Now on startup the ssb gets removed and after that the new wl gets  inserted. Adding wl to the /etc/modules will not help because the  removing needs to be done first.
So with the /etc/rc.local modification everything happens in the correct order for perfect WiFi.

This was tested multiple times on a MacBook Pro with the Broadcom 4328  chipset and should work for all chipsets not supported by the b43  drivers.

Update:
Not all systems include the 'linux/sched.h' file. Install the  'linux-headers-generic' package if you get errors. The generic package  is a meta package that should install the propper package for your  kernel. If it isn't working install with
Code:

sudo apt-get install linux-headers-$(uname -r)

hope this helps
GD

```

but after i process "make", i usually get this error message

```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.39.4/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/src/wl/sys/wl_linux.o
/root/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/root/src/wl/sys/wl_linux.c:486: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/root/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/root] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4'
make: *** [all] Error 2


```

i've do the prepare kernel sources and install the linux generic header to prevent such as error compiling..

please help me :)

---

