---
title: "Is 2.6.15-23 the last kernel upgrade for 6.06?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2006-06-03
I was just wondering, will 2.6.15-23 be the last kernel upgrade for Dapper/6.06 LTS?

So if I ever want to see 2.6.16 I'll have to go to Edgy?

I just want to know that I'll never have to recompile things again on my Dapper box.

---

### Post by llamakc on 2006-06-03
If you run one of these:

linux-image-386 - Linux kernel image on 386.
linux-image-686 - Linux kernel image on PPro/Celeron/PII/PIII/PIV.
linux-image-k7 - Linux kernel image on AMD K7.

They'll always point to the most-recent kernel version available in the repositories. 

Similarly, linux-source does the same thing.

ken@vulva:~$ apt-cache show linux-source
Package: linux-source
Priority: optional
Section: devel
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Source: linux-meta
Version: 2.6.15.22
Depends: linux-source-2.6.15
Filename: pool/main/l/linux-meta/linux-source_2.6.15.22_all.deb
Size: 23310
MD5sum: 553b714a01d103daa3ce8ee4bff6c748
Description: Linux kernel source with Ubuntu patches
 This package will always depend on the latest Linux kernel source code
 available. The Ubuntu patches have been applied.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

But as you see above its only fetching 2.6.15.22 and not .23 which the compiled linux-image is on right now (I'm running 2.6.15-23-k7).

---

### Post by kacheng on 2006-06-03
I see thanks, but what I want to know is if there are plans to have a newer kernel in Dapper, or are we frozen at 2.6.15-23 (which I would prefer) for the next 3 years.

---

### Post by Teroedni on 2006-06-03
Its seems were frozen.
I have astleast not seen any newer kernel version (running amd 64 k8 2.6.15-23)

---

### Post by kacheng on 2006-06-08
Can anyone else confirm?

---

