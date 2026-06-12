---
title: "C++ compiler cannot create executables."
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by jackconstantine on 2005-10-02
trying to install a few different things (specifically nVidia drivers and MusicBrainz), and ran into this problem.  Terminal snippets:

[i]root@res05-jfdr:/home/jackconstantine/Desktop/musicbrainz-1.1.0 # ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc -Wall -O2 ) works... yes
checking whether the C compiler (gcc -Wall -O2 ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.[/i]

Thanks, ladies and gentlemen.

---

### Post by jackconstantine on 2005-10-02
Oh, also: from synaptic package manager (where I installed gcc), the following packages are installed:
gcc
gcc-3.3
gcc-3.3-base
libgcc1

---

### Post by Biased turkey on 2005-10-03
Did you install the build-essential package with:
sudo apt-get install build-essential

That package is ... essential :) if you want to use the C, C++ compiler
See that link
[https://wiki.ubuntu.com/InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers")

---

