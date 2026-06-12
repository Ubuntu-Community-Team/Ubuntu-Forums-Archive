---
title: "ISO Problems"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by spandey on 2010-12-25
Hi,
I am in India and downloaded  the default 32bit ISO file for 10.10. After Installing I had problems with flash and many other issues.

when I  "Uname -m" it says i686. I booted the Live CD it also says i686 for uname -m.

How can I download the proper 32 bit ISO using WGET?

---

### Post by efflandt on 2010-12-25
i686 "is" the 32-bit version.  It refers to certain classes of processors (CPUs).  That should work for Pentium Pro or newer if you have enough RAM. [http://en.wikipedia.org/wiki/P6_%28microarchitecture%29](http://en.wikipedia.org/wiki/P6_%28microarchitecture%29)

You have not said what hardware you have, whether you are using anything other than default video drivers, or any details about what problems you are having.  Sometimes flash problems are caused by having too many conflicting flash plugins.  Normally the only one package you should have related to flash is flashplugin-installer (which is included if you install ubuntu-restricted-extras or other *ubuntu-restricted-extras).  If you also have gnash, that may result in problems.

If you have an old slow computer, slow internet connection, and/or not enough RAM, flash videos may have a slow frame rate or may actually pause frequently.

What shows for the video (VGA) section if in a terminal you do: **sudo lspci -v**

---

### Post by spandey on 2010-12-25
Thanks for i386/686 info. 

I have Intel dg31pr motherboard, 3gb ddr2 ram, 250 gb SATA hard disk, Intel core2duo E7600, Integrated Graphics(No Graphics card)

Some observations, after Updates. Now if I go in menu and About Ubuntu it says Ubuntu 11.04 - the Natty Narwhal. Where as I have installed 10.10.  Here is my VGA ...

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation 82G33/G31 Express Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at ff900000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at f140 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at ff700000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

---

