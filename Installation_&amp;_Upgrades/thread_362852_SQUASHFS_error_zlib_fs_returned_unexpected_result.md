---
title: "SQUASHFS error: zlib_fs returned unexpected result"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by zipeppe on 2007-02-16
Dear all,

here's ZpP.

I've trouble installing ubuntu 7.04 herd3 on may desktop system, a bit outdated but working system (mobo Gigabyte GA-8PE667, Intel P4 2.4GH, 1 GB TwonMOS RAM, HDD Hitachi PATA HDS722512VLAT20 120GB as master & HDD Western Digital PATA WDCWD800BB-00CAA1 80 GB as slave on primary IDE, IDE-CD R/RW 16x10A on secondary IDE, nVidia GeForce 4600ti) .

The installation process hangs at the boot time. So far as I see all 
the hardware is correctly recognized, nevertheless the next message appears 
(splash and quite mode disabled):

.
.
.
loop: loaded
[37.173779] SQUASHFS error: Unable to read cache block [270bf206:141e]
                       SQUASHFS error: zlib_fs returned unexpected result 0xFFFFFFFF
[37.173779] SQUASHFS error: Unable to read cache block [270bf206:141e]
                       SQUASHFS error: zlib_fs returned unexpected result 0xFFFFFFFF
[37.173779] SQUASHFS error: Unable to read cache block [270bf206:141e]
                       SQUASHFS error: zlib_fs returned unexpected result 0xFFFFFFFF
[37.173779] SQUASHFS error: Unable to read cache block [270bf206:141e]
                       SQUASHFS error: zlib_fs returned unexpected result 0xFFFFFFFF.
.
.

The iso' md5sum is correct and the image has been burnt at 4X many and many times!

No problem booting with other distros, as openSUSE 10.2...

Any idea about this problem?

:lolflag:

---

### Post by zipeppe on 2007-02-17
up

---

