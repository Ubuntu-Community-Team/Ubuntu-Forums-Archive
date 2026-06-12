---
title: "wubi installation of ubuntu 12.10"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by coolguysraju on 2012-11-10
I have recently installed ubuntu 12.10 32 bit from wubi with window 8 as main os then i wanted ti upgrade ubuntu from 12.10 32bit to 64 bit  during installation of 12.10 64 bit it always show error showing that root.disk is already available  so it can't progress after that can anybody help me from this ,plz.......

---

### Post by westie457 on 2012-11-10
Take a look at this old thread. It might help in some way.

[http://ubuntuforums.org/showthread.php?t=849183](http://ubuntuforums.org/showthread.php?t=849183)

---

### Post by cwsnyder on 2012-11-10
One possible gotcha: Windows 8 64-bit would be able to properly host WUBI 12.10 64-bit or 32-bit; Windows 8 32-bit would probably NOT host WUBI 12.10 64-bit.

---

### Post by Karlchen on 2012-11-10
> **cwsnyder said:**
> One possible gotcha: Windows 8 64-bit would be able to properly host WUBI 12.10 64-bit or 32-bit; Windows 8 32-bit would probably NOT host WUBI 12.10 64-bit. It is extremely unlikely that Windows 8 32-bit will refuse to host Ubuntu 64-bit.

Windows 32-bit and Windows 64-bit use exactly the same type of NTFS filesystem. A Ubuntu Wubi installation only uses the NTFS filesystem in order to store its root.disk and swap.disk files. Apart from that both operating systems are pretty independent.

For a short while I had Wubi installed Ubuntu 12.04 64-bit up and running on a Window 7 32-bit machine.

Karl

---

### Post by Frogs Hair on 2012-11-10
Wubi downloads 64 bit by default. See the guide for 32 bit installation. The guide may not be applicable to Win 8 because it is so new. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

