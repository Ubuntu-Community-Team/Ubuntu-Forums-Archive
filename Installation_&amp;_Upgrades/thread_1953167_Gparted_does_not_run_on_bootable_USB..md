---
title: "Gparted does not run on bootable USB."
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by Seishuku on 2012-04-05
I'm tying to install Ubuntu 10.04LTS on my Acer Aspire One, which was recently reset to factory settings after having some sort of motherboard problems (a techie friend of the family brought it back from the dead).  The Windows XP freezes up quite a bit and I'm hoping it won't  have that problem on Ubuntu.  After having failed with two other drives, I made a bootable USB.  However, when I try to run the installer it stops running after hitting "next" on the keyboard part, and gparted crashes if I try to run it on its own.

This is what happens when I run it from the terminal:
```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0x11af0a]
  15: /lib/libparted.so.0(+0x42617) [0x152617]
  14: /lib/libparted.so.0(+0x43427) [0x153427]
  13: /lib/libparted.so.0(+0x4471c) [0x15471c]
  12: /lib/libparted.so.0(+0xf7b1) [0x11f7b1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x123032]
  10: /lib/libparted.so.0(+0x460b3) [0x1560b3]
  9: /lib/libparted.so.0(+0x462af) [0x1562af]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x123e15]
  7: /usr/sbin/gpartedbin() [0x80901e6]
  6: /usr/sbin/gpartedbin() [0x809fc9b]
  5: /usr/sbin/gpartedbin() [0x80c0532]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0xa04eb2]
  3: /lib/libglib-2.0.so.0(+0x65def) [0x37bdef]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0x41c96e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x5a9a4e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.
```I don't know what's wrong or how I can fix this.  Is there something wrong with my hard drive that it can't read the partitions?

---

### Post by Seishuku on 2012-04-05
A friend of mine who's helping figured out that the reason it's crashing is because it can't read the USB.  He told me to run "gksudo gparted /dev/sda" and then gparted worked just fine.  But then, I'd have to find away to specifiy the hard drive when installing Ubuntu...

Or maybe I should reformat the USB or try a different USB maybe?

---

