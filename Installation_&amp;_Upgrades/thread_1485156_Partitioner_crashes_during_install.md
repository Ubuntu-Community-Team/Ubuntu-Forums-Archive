---
title: "Partitioner crashes during install"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by crazedmobofphilosophers on 2010-05-16
[SIZE=2]hello!

The disk partitioner crashes while installing Ubuntu 10.04 on a Dell Inspiron 5100 (32 bit x86). The disk has two partitions, a 50 gig windows xp and a 100 gig Linux Mint.

I tried running Gparted in the terminal and it returned:[/SIZE]

[SIZE=1]ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0x1a1f4a]
  15: /lib/libparted.so.0(+0x424b7) [0x1d94b7]
  14: /lib/libparted.so.0(+0x432c7) [0x1da2c7]
  13: /lib/libparted.so.0(+0x445bc) [0x1db5bc]
  12: /lib/libparted.so.0(+0xf7f1) [0x1a67f1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x1aa072]
  10: /lib/libparted.so.0(+0x45f53) [0x1dcf53]
  9: /lib/libparted.so.0(+0x4614f) [0x1dd14f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x1aae55]
  7: /usr/sbin/gpartedbin() [0x80901d6]
  6: /usr/sbin/gpartedbin() [0x809fc8b]
  5: /usr/sbin/gpartedbin() [0x80c0522]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0x8d5eb2]
  3: /lib/libglib-2.0.so.0(+0x65dcf) [0x73fdcf]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0x11b96e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x1082a0e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.
[/SIZE]
[SIZE=2]Any help would be appreciated, thanks in advance![/SIZE]

---

### Post by srs5694 on 2010-05-16
Try posting the output of "sudo fdisk -lu". Please post the results between a "[noparse]```
[/noparse]" string and a "[noparse]
```[/noparse]" string to improve legibility.

---

