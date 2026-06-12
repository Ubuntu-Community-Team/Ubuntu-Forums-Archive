---
title: "make command error while installing kernel"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Sikandar on 2010-02-18
I currently have 2.6.28-18 version and linux distribution is ubuntu 9.04 while installing kernel 2.6.30; everything is going fine till make oldconfig.
But am getting following error after **make** command: 
> sh /usr/src/linux-headers-2.6.28-18-generic/arch/x86/boot/install.sh 2.6.28.10 arch/x86/boot/bzImage System.map "/boot"

*** Missing file: arch/x86/boot/bzImage
*** You need to run "make" before "make install".

make[1]: *** [install] Error 1
make: *** [install] Error 2

---

