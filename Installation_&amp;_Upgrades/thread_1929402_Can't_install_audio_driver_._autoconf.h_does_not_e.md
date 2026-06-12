---
title: "Can't install audio driver . autoconf.h does not exist"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by arunkumarrathore on 2012-02-22
I want to install alsa-driver for my ubuntu 11.04 but a error occured : autoconf.h does not exist & this msg appears :


root@rathore-system:~/Desktop/Audio/alsa-driver-1.0.12-4.05b# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /root/Desktop/Audio/alsa-driver-1.0.12-4.05b
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.38-8-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
[B][U]checking for kernel linux/autoconf.h... no
The file /lib/modules/2.6.38-8-generic/build/include/linux/autoconf.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel[/U][/B]
sources (default is /lib/modules/2.6.38-8-generic/build).
root@rathore-system:~/Desktop/Audio/alsa-driver-1.0.12-4.05b#

---

### Post by nitin.pant on 2012-07-01
I have the same problem. I have the dell creative sound card detected on my linux box but i reinstalled alsa and thats when this problem occured...

I get the exact same error while installing alsa...

I purged and installed the kernel image but to no help.
Anybody?

---

