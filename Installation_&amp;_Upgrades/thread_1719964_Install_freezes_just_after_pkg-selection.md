---
title: "Install freezes just after pkg-selection"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by xodeus on 2011-04-02
Hi there.
I've tried to install several ubuntu/debian based variants for the last 3 weeks. But without any luck. I'm running arch linux right now, which my brother somehow managed to install. Everytime I try to install I'm stuck at this screen:
[ATTACH]187892[/ATTACH]
I don't get any error messages or anything.

Distros tried:
Ubuntu 10.10
Ubuntu 11.04

Crunchbang (debian based, same installer)

Elementary (same installer, ubuntu based)

I've difficulties starting gparted everytime, so I think this is due to some errors with my harddrive and I'm ready to fully wipe it to start over, if anyone could help with that.

RESULTS.txt from bootinfo attatched.
[ATTACH]187893[/ATTACH]

Here's some info from Terminal when trying to start GParted.
```
me@elementary:~$ sudo gparted
======================
libparted : 2.3
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0x25187a]
  15: /lib/libparted.so.0(+0x41337) [0x289337]
  14: /lib/libparted.so.0(+0x42157) [0x28a157]
  13: /lib/libparted.so.0(+0x4344c) [0x28b44c]
  12: /lib/libparted.so.0(+0xe161) [0x256161]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x2599f2]
  10: /lib/libparted.so.0(+0x44ea5) [0x28cea5]
  9: /lib/libparted.so.0(+0x450af) [0x28d0af]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x25a7d5]
  7: /usr/sbin/gpartedbin() [0x80900b6]
  6: /usr/sbin/gpartedbin() [0x809beb5]
  5: /usr/sbin/gpartedbin() [0x80c1dd2]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x141e42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0xbde48f]
  2: /lib/libpthread.so.0(+0x5cc9) [0x175cc9]
  1: /lib/libc.so.6(clone+0x5e) [0xeea69e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function probe_partition_for_geom() failed.
me@elementary:~$ 

```

Hope that anyone can help

---

### Post by Dutch70 on 2011-04-02
It would be nice it you edited your post and put the contents of the results.txt info between code tags also. :D

The only things I can tell you so far is...
1.) 10.10 has issues with some usb sticks, try 10.04 and it should work...or a different usb stick.
2.) Your boot info script shows grub legacy is installed. 10.10 & 11.04 use Grub2, as well as 10.04. 
Although I don't think it matters right now, since you don't actually have Ubuntu installed.

---

### Post by xodeus on 2011-04-02
So the only option is to install from a CD media?

---

### Post by Dutch70 on 2011-04-02
I don't know if that would help you either, I'd try 10.04 from the usb.

---

