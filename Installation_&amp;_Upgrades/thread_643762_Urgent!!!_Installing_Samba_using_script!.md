---
title: "Urgent!!! Installing Samba using script!"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by salvor_hardin on 2007-12-18
Hello!

I have installed Samba without problems using apt-get install, but now i need to make installation script for computers wothout internet connection. I have Samba directory, i tried to install it by executing ./configure script in its source directory. This is output that I get: 

SAMBA VERSION: 3.0.28
LIBREPLACE_LOCATION_CHECKS: START
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
LIBREPLACE_LOCATION_CHECKS: END
LIBREPLACE_CC_CHECKS: START
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

Log file attached!

Using ./configure --help i realized I need to put some extra variables or something in command. Please help! What do I have to do. 

Ubuntu 6.06 LTS

---

### Post by wharp on 2007-12-18
There are several threads on this already.  I had this issue at one point, but i don't remember what my fix was.  Make sure you have build-essential installed, as well as the ia32* libs.  

Also, do a search on the forums for that error message and you should get a number of threads.

---

