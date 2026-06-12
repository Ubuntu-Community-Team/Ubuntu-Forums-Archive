---
title: "Just Upgraded to Ubuntu 10.10 and my VMware Wrokstation Stoped Working."
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by judoka1113 on 2010-10-11
What do I do to fix my VMware Workstation after I upgraded Ubuntu 10.04 t0 10.10.  It said that I needed to compile and reinstall a few modules in to the running kernel. Than it fails to do it and tells me to look in the file from which the output is:  $ sudo cat  /tmp/vmware-root/setup-6801.log   Oct 10 21:51:33.262: app-140341270488832| Log for VMware Workstation pid=6801 version=7.1.0 build=build-261024 option=Release Oct 10 21:51:33.262: app-140341270488832| The process is 64-bit. Oct 10 21:51:33.262: app-140341270488832| Host codepage=UTF-8 encoding=UTF-8 Oct 10 21:51:33.262: app-140341270488832| Logging to /tmp/vmware-root/setup-6801.log Oct 10 21:51:33.399: app-140341270488832| modconf query interface initialized Oct 10 21:51:33.400: app-140341270488832| modconf library initialized Oct 10 21:51:33.437: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.448: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.462: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.485: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.500: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.553: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.558: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.562: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.566: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.570: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.601: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.605: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.609: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.613: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.617: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.625: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.641: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.696: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.700: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.704: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.708: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.712: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.721: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.736: app-140341270488832| Your GCC version: 4.4 Oct 10 21:51:33.813: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.817: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.821: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.825: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:33.829: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:34.083: app-140341270488832| Trying to find a suitable PBM set for kernel 2.6.35-22-generic. Oct 10 21:51:34.084: app-140341270488832| Building module vmmon. Oct 10 21:51:34.084: app-140341270488832| Extracting the sources of the vmmon module. Oct 10 21:51:34.103: app-140341270488832| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5 Oct 10 21:51:37.289: app-140341270488832| Failed to compile module vmmon!    What do I do to fix this?

---

### Post by judoka1113 on 2010-10-11
Found a good link that solved a problem [https://answers.launchpad.net/vmware-ubuntu/+question/128677](https://answers.launchpad.net/vmware-ubuntu/+question/128677)

---

### Post by chasem1991 on 2010-10-11
Thanks!

Helped me get it working.

---

### Post by md10 on 2010-10-13
Did not work for me. Is there any (easy) way to get back to 10.04?

tnx

Solved by installing the patch command

---

