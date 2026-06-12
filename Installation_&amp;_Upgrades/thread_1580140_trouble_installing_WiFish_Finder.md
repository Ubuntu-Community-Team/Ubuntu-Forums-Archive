---
title: "trouble installing WiFish Finder"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by Brian Keith on 2010-09-22
downloaded zip file, unzipped it, folder contains: 
common.c  crctable_osdep.h  linux.o    network.h  osdep.h common.h  libosdep.a        Makefile   network.o  osdep.o
common.o  linux.c  network.c  osdep.c      packed.h

ran make command, returns the following:
make -C osdep
make[1]: Entering directory `/home/brian/Downloads/WiFishFinder-v0.2/osdep'
Building for Linux
make[2]: Entering directory `/home/brian/Downloads/WiFishFinder-v0.2/osdep'
make[2]: `.os.Linux' is up to date.
make[2]: Leaving directory `/home/brian/Downloads/WiFishFinder-v0.2/osdep'
make[1]: Leaving directory `/home/brian/Downloads/WiFishFinder-v0.2/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64  -Iinclude   -c -o wifishfinder.o wifishfinder.c
cc1: warnings being treated as errors
wifishfinder.c: In function ‘main’:
wifishfinder.c:3191: error: format not a string literal and no format arguments
wifishfinder.c:3203: error: format not a string literal and no format arguments
make: *** [wifishfinder.o] Error 1

can anyone help? thanks

---

