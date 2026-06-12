---
title: "change to smp kernel and nvidia driver dies"
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by dmallery on 2005-05-10
I have been running this dual athlon machine for several weeks on a non-smp kernel.  I installed many of the things in the starter guide, including the nvidia driver.

this morning i installed the linux-image-2.6.10-5-k7-smp kernel.  works fine.
gdm dies because it can't find the nvidia image, which is there.  or is it a different module directory??  i have tried dpkg-reconfigure and verified that everything in the starter guide is as advertised.

thanks in advance for any pointers

dave mallery

---

### Post by Xian on 2005-05-10
Try installing the restricted-modules for your kernel:
$sudo apt-get linux-restricted-modules-2.6.10-5-k7-smp

Might then have to reinstall nvidia package....,

---

### Post by dmallery on 2005-05-11
many many thanks!

i didn't have to re-install, just make the change in xorg.conf from "nv" back to "nvidia"

dave mallery

---

