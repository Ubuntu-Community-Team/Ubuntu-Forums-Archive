---
title: "change the driver file and compile the kernel"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by cccc on 2011-05-09
hi

I must change the driver file manually and compile the kernel.
Are these steps OK, or pls correct me:

# mkdir ~/newkernel/

# cp /usr/src/linux-source-2.6.35.tar.bz2 ~/newkernel/

# tar xjf linux-source-2.6.35.tar.bz2

# cd linux-source-2.6.35

# cp -vi /boot/config-`uname -r` .config

# make oldconfig

# make localmodconfig

change driver file manually

# fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers

---

