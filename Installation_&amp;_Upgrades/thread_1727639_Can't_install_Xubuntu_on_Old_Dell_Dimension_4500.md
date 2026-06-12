---
title: "Can't install Xubuntu on Old Dell Dimension 4500"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by Adrastus on 2011-04-12
[FONT=Arial][SIZE=3]Hi all,

I'm trying to install Xubuntu on an old Dell Dimension 4500:
[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=3]756 MB RAM[/SIZE][/FONT]
[*][FONT=Arial][SIZE=3]ATI Radon 9600 Pro gfx card[/SIZE][/FONT]
[*][FONT=Arial][SIZE=3]Pentium 4 1.8 GHz CPU[/SIZE][/FONT]
[*][FONT=Arial][SIZE=3]old 300 GB HDD from a friend[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=3]I've been running it off of a flash drive for some time now and I'd like to just try and install it now that I have an actual hard drive.  I've tried both CDs (Ubuntu 10.04 and 10.10 as well as Kubuntu 10.10) and they usually get to the point where it starts to reformat the drive and then it just freezes.  With the USB stick I can use the live session just fine but when I try to install Xubuntu Gparted crashes and it doesn't get any further.

Terminal output:

[/SIZE][/FONT]```
ubuntu@ubuntu:~$ gksu gparted&
[1] 5760
ubuntu@ubuntu:~$ ======================
libparted : 2.3
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xcb687a]
  15: /lib/libparted.so.0(+0x41337) [0xcee337]
  14: /lib/libparted.so.0(+0x42157) [0xcef157]
  13: /lib/libparted.so.0(+0x4344c) [0xcf044c]
  12: /lib/libparted.so.0(+0xe161) [0xcbb161]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xcbe9f2]
  10: /lib/libparted.so.0(+0x44ea5) [0xcf1ea5]
  9: /lib/libparted.so.0(+0x450af) [0xcf20af]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xcbf7d5]
  7: /usr/sbin/gpartedbin() [0x80900b6]
  6: /usr/sbin/gpartedbin() [0x809beb5]
  5: /usr/sbin/gpartedbin() [0x80c1dd2]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x185e42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0x26148f]
  2: /lib/libpthread.so.0(+0x5cc9) [0xa88cc9]
  1: /lib/libc.so.6(clone+0x5e) [0xb6d69e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function probe_partition_for_geom() failed.
```[FONT=Arial][SIZE=3]

What now?  Are there any log files that would help?

--Adrastus

[/SIZE][/FONT]

---

