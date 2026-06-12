---
title: "EMBOSS installing issues"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by ElsassBlitz on 2013-02-08
Hello everybody,
I want to install EMBOSS 6.5.7 on Ubuntu 12.04 LTS. I unpacking and do the "./configure". After that, the "make" command doesn't work:

> sebastien@ubuntu:~/Bureau/Devoir 1/EMBOSS-6.5.7$ make
Making all in plplot
make[1]: entrant dans le répertoire « /home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7/plplot »
Making all in lib
make[2]: entrant dans le répertoire « /home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7/plplot/lib »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7/plplot/lib »
make[2]: entrant dans le répertoire « /home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7/plplot »
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../ajax/core  -I../ajax/core  -I./ -I/usr/include/gd -DPREFIX=\"/usr/local\" -DBUILD_DIR=\".\" -DDRV_DIR=\".\" -DEMBOSS_TOP=\"/home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7\" -DAJ_LinuxLF -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64  -O2  -MT pdfutils.lo -MD -MP -MF .deps/pdfutils.Tpo -c -o pdfutils.lo pdfutils.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../ajax/core -I../ajax/core -I./ -I/usr/include/gd -DPREFIX=\"/usr/local\" -DBUILD_DIR=\".\" -DDRV_DIR=\".\" -DEMBOSS_TOP=\"/home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7\" -DAJ_LinuxLF -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -MT pdfutils.lo -MD -MP -MF .deps/pdfutils.Tpo -c pdfutils.c  -fPIC -DPIC -o .libs/pdfutils.o
gcc: error: 1/EMBOSS-6.5.7": No such file or directory
make[2]: *** [pdfutils.lo] Erreur 1
make[2]: quittant le répertoire « /home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7/plplot »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/sebastien/Bureau/Devoir 1/EMBOSS-6.5.7/plplot »
make: *** [all-recursive] Erreur 1=Someone may help me please?
Thank you very much!

---

### Post by ElsassBlitz on 2013-02-09
Hello,
on the French ubuntu forum, someone has found  the answer. The issue comes from:
```
[…] gcc: error: 1/EMBOSS-6.5.7": No such file or directory […]
```Just need to remove the space between "Devoir" and "1" on my directory, that's the problem.
I hope that this post can help other peoples! 
Thank you.

---

