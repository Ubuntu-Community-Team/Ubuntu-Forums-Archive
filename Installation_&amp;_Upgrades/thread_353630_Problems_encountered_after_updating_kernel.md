---
title: "Problems encountered after updating kernel"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by trenog on 2007-02-04
Hello. Well I encountered this problem after successfully getting my usb networking device to work with ndiswrapper. I had installed automatix and downloaded/installed a bunch of stuff with it, after which point I restarted the system. When grub loaded up it listed now not only the 2.6.15-26-386 kernel but the 2.6.15-27-386 kernel. I loaded the newer kernel and found that my wlan connection was missing from the networking list, despite the fact that ndiswrapper seemed to be installed still along with the drivers. I tried to repeat the installation process but received an error when I had tried to perform $ sudo modprobe ndiswrapper.

I had figured that maybe something was wrong with the build so I tried to make it again. I ran into this error after:

```

make -C driver
make[1]: Entering directory '/home/trenog/Desktop/ndiswrapper-1.35/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
    give the path to kernel build directory with
    KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/trenog/Desktop/ndiswrapper-1.35/driver'
make: *** [all] error 2

```

And one other thing that seems to have gone wrong is that my 2.6.15-26-386 kernel locks up when it tries to configure network connections, specifically the line it hangs on is:

```
[17179597.852000] ndiswrapper version 1.35 loaded (preempt=yes, smp=no)
```

I'd like to get back to a build that has working internet but I have no idea how to make it happen again. Do I need to manually download and install packages to my newer kernel or do I need to fix my older one?

Thanks

---

### Post by trenog on 2007-02-05
Alright, I managed to solve this problem myself.

I first downloaded the linux-headers 2.6.15-27 and linux-headers 2.6.15-27-386 deb files, unpacked the first one, then the second one, uninstalled the ndiswrapper make, remade it, installed it, uninstalled the drivers, reinstalled the drivers, and redid the last steps necessary for getting the wrapper to work.

I now sit posting in the new kernel.

Heh. This OS might just start growing on me.

---

