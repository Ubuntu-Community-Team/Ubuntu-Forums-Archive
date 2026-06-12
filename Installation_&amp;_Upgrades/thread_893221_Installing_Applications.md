---
title: "Installing Applications"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Jeremywilms on 2008-08-18
I'm trying to install GCC correctly, but when I try to use the ./configure command I don't get the output I want.

> cjeremy@jeremy-desktop:~$ cd /home/jeremy/Desktop/gcc-4.3.1
jeremy@jeremy-desktop:~/Desktop/gcc-4.3.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gnatbind... no
checking for gnatmake... no
checking whether compiler driver understands Ada... no
checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for correct version of gmp.h... no
configure: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+.
Try the --with-gmp and/or --with-mpfr options to specify their locations.
Copies of these libraries' source code can be found at their respective
hosting sites as well as at [ftp://gcc.gnu.org/pub/gcc/infrastructure/](ftp://gcc.gnu.org/pub/gcc/infrastructure/).
See also [http://gcc.gnu.org/install/prerequisites.html](http://gcc.gnu.org/install/prerequisites.html) for additional info.
If you obtained GMP and/or MPFR from a vendor distribution package, make
sure that you have installed both the libraries and the header files.
They may be located in separate packages.


---

### Post by Jeremywilms on 2008-08-18
I got it to work via installing the GMP and MPFR libraries. Thanks anyway guys.

---

