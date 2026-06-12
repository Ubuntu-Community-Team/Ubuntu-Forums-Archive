---
title: "Problems with kernel and headers 2.6.33"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Achtung_swe on 2010-08-04
Hi

I recently bought a new laptop and decided to put an SSD drive in it. After reading on the internet I realised I need the 2.6.33 kernel to be able to run TRIM. The only problem was that I couldnt find this kernel in the usual repositories in Synaptic or KPackageKit. The only place I could find it was here [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
So I manually downloaded the kernel along with the headers(both the "All" one and the "amd64" verion) and after some trouble I managed to install and boot the new Kernel. So far so good but here comes the problem: in order to use my network card I need to compile the driver with the new Kernel(i.e the "make" command) but when I try I get an error saying "missing autoconf.h". I am kind of a noob when it comes to installing new Kernels manually so maybe this is an effect of my manual fiddling or am I missing something when I try to upgrade my Kernel(is this the standard procedure when wanting to upgrade to a newer kermel than the one in the newest release? It feels like there should be some repository which contains all the newer kernels and their headers but I couldnt find one).
 Any help is much appreciated.

Thanks

---

### Post by lemming465 on 2010-08-07
If you are installing custom-built kernels, you need the build toolchain.  An easy way to pull in most of the stuff you might need is *apt-get install wireshark-dev*; that has a splendid dependency list.

---

