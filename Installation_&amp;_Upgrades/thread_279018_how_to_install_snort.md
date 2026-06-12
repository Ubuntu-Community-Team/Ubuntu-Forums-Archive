---
title: "how to install snort?"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by necron_09 on 2006-10-17
i try to write this step....


linux@ubuntu:~$ cd Desktop
linux@ubuntu:~/Desktop$ cd snort-2.6.0.2
linux@ubuntu:~/Desktop/snort-2.6.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
strife@ubuntu:~/Desktop/snort-2.6.0.2$

then it shows this error, how do i solve it?? please help me for the problem :*( ....

---

### Post by dannyboy79 on 2006-10-17
did you do what it says? See `config.log' for more details? Also, do you have the build-essentials package installed which is required for compiling stuff from source?

---

