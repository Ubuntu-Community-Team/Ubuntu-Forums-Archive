---
title: "Kernel panic after update"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by Sendervictorius on 2012-06-22
The most recent update fails after updating to kernel 3.2.0.25.27. I get "Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)" when booting.

I can successfully boot by choosing a previous kernel from grub.

How do I fix the update? do i just uninstall and reinstall the kernel?

---

### Post by dino99 on 2012-06-23
i've never found a better kernel than the 3.5.1 or 3.4.4

erase your faulty one and install a newer one into an empty folder: 

choose between i386 (32 bits) or amd64 (64 bits) and download the 4 debs: 
- linux-headers........all.deb
- linux-headers........deb (here choose between i386 & amd64)
- linux-image...........deb  ( " " )
- linux-image-extra......deb ( " " )

scroll down the page : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

when the downloads are done, open a terminal to run:

cd to the folder where the kernel downloaded files are, and

sudo dpkg -i *

---

