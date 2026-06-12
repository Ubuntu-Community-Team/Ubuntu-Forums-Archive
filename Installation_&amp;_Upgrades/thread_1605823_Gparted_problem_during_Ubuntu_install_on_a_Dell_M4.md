---
title: "Gparted problem during Ubuntu install on a Dell M4500"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by skhelladi on 2010-10-25
Hi,
The installation of ubuntu on a dell m4500 fails at the step of loading gparted. At the beginning I thought that the problem is the ubuntu version, I tried 10.04 (with a known problem of graphic card, I knew how to bypass it) and then 10.10 with the same result: gparted fails to be loaded... I test also gparted alone (live-cd), the problem is the same :(

Have you any idea about the possible source of this problem?

Is it a problem of the hard drive? it is set at "Raid on" the bios options.

Thanks by advance.

The configuration I have is:
-Dell Precision M4500
-Intel Core i7-820QM(1.73GHz,8MB,Quad Core,45W)
-8GB(2x4GB)1333MHz DDR3 Dual Channel
-500GB Serial ATA (7,200 Rpm)
-1 Go NVIDIA Quadro FX 880M

N.B: 
I speak about the ubuntu install, the "try ubuntu without install" option works very well, all disc partitions are detected and every thing seems ok.

---

### Post by sikander3786 on 2010-10-25
Try nodmraid parameter from F6 options on the first screen. Instructions here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Sometimes removing dmraid package also helps.

```
sudo apt-get remove dmraid
```

If it still doesn't, try starting gparted from terminal and post the messages, if you see any.

```
gksudo gparted
```

P.S How many Sata controllers are there?

---

### Post by ronparent on 2010-10-25
Do you get the same results by installing from the live cd session?

---

### Post by skhelladi on 2010-10-26
thank you sikander3786, I will try what you suggested and let you know.

> **sikander3786 said:**
> Try nodmraid parameter from F6 options on the first screen. Instructions here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Sometimes removing dmraid package also helps.

```
sudo apt-get remove dmraid
```If it still doesn't, try starting gparted from terminal and post the messages, if you see any.

```
gksudo gparted
```P.S How many Sata controllers are there?

---

### Post by skhelladi on 2010-10-26
yes the result is the same when using the live cd session.

> **ronparent said:**
> Do you get the same results by installing from the live cd session?

---

### Post by skhelladi on 2010-10-26
first I tested "nodmraid" didn't work and then I removed "dmraid", it didn't work too :( the message given by gparted is :

======================
libparted : 2.3
======================
Backtrace has 15 calls on stack:
  15: /lib/libparted.so.0(ped_assert+0x31) [0x7f8f3b7f85c1]
  14: /lib/libparted.so.0(+0x392f6) [0x7f8f3b8232f6]
  13: /lib/libparted.so.0(+0x39a73) [0x7f8f3b823a73]
  12: /lib/libparted.so.0(+0x3a72d) [0x7f8f3b82472d]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x1cb) [0x7f8f3b7fed3b]
  10: /lib/libparted.so.0(+0x3bc74) [0x7f8f3b825c74]
  9: /lib/libparted.so.0(+0x3be65) [0x7f8f3b825e65]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x7f8f3b7ff815]
  7: /usr/sbin/gpartedbin() [0x44a884]
  6: /usr/sbin/gpartedbin() [0x45a721]
  5: /usr/sbin/gpartedbin() [0x477ec7]
  4: /usr/lib/libglibmm-2.4.so.1(+0x383f2) [0x7f8f3a27d3f2]
  3: /lib/libglib-2.0.so.0(+0x697e4) [0x7f8f396c67e4]
  2: /lib/libpthread.so.0(+0x7971) [0x7f8f38ca8971]
  1: /lib/libc.so.6(clone+0x6d) [0x7f8f38a0492d]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function probe_partition_for_geom() failed.

 


> **sikander3786 said:**
> Try nodmraid parameter from F6 options on the first screen. Instructions here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Sometimes removing dmraid package also helps.

```
sudo apt-get remove dmraid
```If it still doesn't, try starting gparted from terminal and post the messages, if you see any.

```
gksudo gparted
```P.S How many Sata controllers are there?

---

### Post by skhelladi on 2010-10-26
the problem is solved by changing the usb key!!!

---

