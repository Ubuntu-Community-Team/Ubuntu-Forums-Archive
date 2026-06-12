---
title: "configure: error: &quot;cannot find libjpeg support&quot;
&quot;cannot find libjpeg support&quot;"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by ganja4u2 on 2005-10-06
I am trying Linux for the first time to broaden my experience, being a Microsoft DOS and Windows user all my life, but when trying to install an HP Laserjet 2300L printer and following the instructions to run the following command I keep getting...."cannot find libjpeg support".  Please help me to install this printer.  I am also using this printer through a D-Link print server with an IP address 192.168.1.10.  I have no problem using this printer through the print server and wireless router when using Windows XP.

$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i586-pc-linux-gnu
checking host system type... i586-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pthread_create in -lpthread... yes
checking for CRYPTO_free in -lcrypto... yes
checking for snmp_timeout in -lnetsnmp... yes
checking for ANSI C header files... (cached) yes
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking net-snmp/net-snmp-config.h usability... yes
checking net-snmp/net-snmp-config.h presence... yes
checking for net-snmp/net-snmp-config.h... yes
checking for an ANSI C-conforming const... yes
checking whether byte ordering is bigendian... no
checking for chkconfig... no
checking for install_initd... found in /usr/lib/lsb
checking for rpm install... no
checking for network build... yes
checking "for cups backend path"... "using /usr/lib/cups/backend"
checking "for icon directory"... "using /usr/lib/menu/hplip"
checking python/Python.h usability... no
checking python/Python.h presence... no
checking for python/Python.h... no
checking python2.2/Python.h usability... no
checking python2.2/Python.h presence... no
checking for python2.2/Python.h... no
checking python2.3/Python.h usability... no
checking python2.3/Python.h presence... no
checking for python2.3/Python.h... no
checking python2.4/Python.h usability... yes
checking python2.4/Python.h presence... yes
checking for python2.4/Python.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
configure: configuring in prnt/hpijs
configure: running /bin/sh './configure' --prefix=/usr  '--prefix=/usr' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for jpeg_set_defaults in -ljpeg... no
configure: error: "cannot find libjpeg support"
configure: error: /bin/sh './configure' failed for prnt/hpijs

---

### Post by mlomker on 2005-10-06
> I am also using this printer through a D-Link print server with an IP address 192.168.1.10.  I have no problem using this printer through the print server and wireless router when using Windows XP.


Almost all IP print servers support LPR, so that shouldn't be a problem.  Have you tried one of the other HP drivers instead?  There isn't much difference between them since they all use PCL.  The only advantage to compiling a driver would be if it has some unique features such as fancy trays, stapling, etc.  If this is just a regular printer with one tray then I wouldn't bother.

That being said, you probably need to download the **libjpeg62-dev** package in Synaptic.

---

### Post by ganja4u2 on 2005-10-07
Thanks

---

