---
title: "Advanced Kernel Modules backporting"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2012-03-14
I am currently running Kernel 3.0.0.17-generic-pae (package: linux-image-generic-pae-lts-backport-oneiric) in 10.04.4-LTS, as of 14 March 2012, and APT gave multiple warnings of missing firmware (which would have been in /lib/firmware, were it available on my local system) related to the ATi®/Advance Micro Devices® Radeon® HD™ series GPU's while setting up the upgrade /boot/vmlinuz and /boot/initrd.img.  All systems were otherwise go, however.  I suspect that the "missing firmware" warnings are related to availability of Kernel Module backports for 10.04.*n*-LTS; SynAPTic™ Package Manager has full module support for Kernel 2.6.32 but not the upgrade Kernel images.

How does one go about installing Modules for upgrade Kernels in an LTS release?  And what PPA's, if any, available for this purpose for Lucid?  I anticipate running 10.04.5-LTS with Kernel 3.2.*n*-generic-pae (package: linux-image-generic-pae-lts-backport-precise) for a short while completing parts acquisitions necessary for a clean install of 12.04.1-LTS.

---

### Post by bcschmerker on 2012-08-30
I upgraded the Everex® to Ubuntu® 12.04.1-LTS, AMD64 Edition, before any Answers were received, which renders this Thread a technical SOLVED. ):P

---

