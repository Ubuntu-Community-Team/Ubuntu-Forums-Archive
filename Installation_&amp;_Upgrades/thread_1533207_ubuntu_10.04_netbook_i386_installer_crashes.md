---
title: "ubuntu 10.04 netbook i386 installer crashes"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by dextro_ on 2010-07-17
I used unetbootin-windows-433.exe and ubuntu-10.04-netbook-i386.iso to make a USB stick and booted from it on my EEE PC 1005HA. The installer works up until I click next on the keyboard layout page at which point I get a "parted_server" error. Here is what I get when I try and run gparted from a terminal.

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0x4ecf4a]
  15: /lib/libparted.so.0(+0x424b7) [0x5244b7]
  14: /lib/libparted.so.0(+0x432c7) [0x5252c7]
  13: /lib/libparted.so.0(+0x445bc) [0x5265bc]
  12: /lib/libparted.so.0(+0xf7f1) [0x4f17f1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x4f5072]
  10: /lib/libparted.so.0(+0x45f53) [0x527f53]
  9: /lib/libparted.so.0(+0x4614f) [0x52814f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x4f5e55]
  7: /usr/sbin/gpartedbin() [0x80901d6]
  6: /usr/sbin/gpartedbin() [0x809fc8b]
  5: /usr/sbin/gpartedbin() [0x80c0522]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0xa65eb2]
  3: /lib/libglib-2.0.so.0(+0x65dcf) [0x24adcf]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0x2b496e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb75a0e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.
Aborted (core dumped)
ubuntu@ubuntu:~
```

---

### Post by ajgreeny on 2010-07-17
Boot from the usb again, but this time hit any key as it starts up and you should get the "Check media" option.  I had a similar problem when I tried to boot from my usb stick the first time, and it turned out the stick was a bad "burn" and not recommended to continue.

---

