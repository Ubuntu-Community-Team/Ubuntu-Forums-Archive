---
title: "Unable to use the &quot;make&quot; command to compile??"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by aoc153 on 2007-09-02
Hi all,

I'm brand new to Ubuntu (or any Linux for that matter), and I'm having a real problem compiling and installing. I've done countless google searches and I just can't seem to get it working.

I first 'cd' to the correct directory and then ./configure (I'll post the log below)

That seems to work fine, but when I type in the make command it gives me the following error:

> 
"make: *** No targets specified and no makefile found.  Stop."

It does this for every program that I try to compile. I've tried many solutions posted on this site and other but none seem to fix it. (build-essential, etc)

Here is the log file when I configure Avant Window Navigator (I'm aware that I don't have the dependencies but I can't install those either):

>   $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = ubuntu
uname -m = i686
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Fri Aug 31 00:55:27 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1574: checking for a BSD-compatible install
configure:1629: result: /usr/bin/install -c
configure:1640: checking whether build environment is sane
configure:1683: result: yes
configure:1748: checking for gawk
configure:1777: result: no
configure:1748: checking for mawk
configure:1764: found /usr/bin/mawk
configure:1774: result: mawk
configure:1784: checking whether make sets $(MAKE)
configure:1804: result: yes
configure:1967: checking how to create a ustar tar archive
configure:1980: tar --version
tar (GNU tar) 1.16
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by John Gilmore and Jay Fenlason.
configure:1983: $? = 0
configure:2023: tardir=conftest.dir && eval tar --format=ustar -chf - "$tardir" >conftest.tar
configure:2026: $? = 0
configure:2030: tar -xf - <conftest.tar
configure:2033: $? = 0
configure:2046: result: gnutar
configure:2053: checking whether to enable maintainer-specific portions of Makefiles
configure:2062: result: no
configure:2093: checking for style of include used by make
configure:2121: result: GNU
configure:2192: checking for gcc
configure:2208: found /usr/bin/gcc
configure:2218: result: gcc
configure:2462: checking for C compiler version
configure:2465: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2468: $? = 0
configure:2470: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2473: $? = 0
configure:2475: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2478: $? = 1
configure:2501: checking for C compiler default output file name
configure:2504: gcc    conftest.c  >&5
configure:2507: $? = 0
configure:2553: result: a.out
configure:2558: checking whether the C compiler works
configure:2564: ./a.out
configure:2567: $? = 0
configure:2584: result: yes
configure:2591: checking whether we are cross compiling
configure:2593: result: no
configure:2596: checking for suffix of executables
configure:2598: gcc -o conftest    conftest.c  >&5
configure:2601: $? = 0
configure:2626: result: 
configure:2632: checking for suffix of object files
configure:2653: gcc -c   conftest.c >&5
configure:2656: $? = 0
configure:2678: result: o
configure:2682: checking whether we are using the GNU C compiler
configure:2706: gcc -c   conftest.c >&5
configure:2712: $? = 0
configure:2716: test -z 
			 || test ! -s conftest.err
configure:2719: $? = 0
configure:2722: test -s conftest.o
configure:2725: $? = 0
configure:2738: result: yes
configure:2744: checking whether gcc accepts -g
configure:2765: gcc -c -g  conftest.c >&5
configure:2771: $? = 0
configure:2775: test -z 
			 || test ! -s conftest.err
configure:2778: $? = 0
configure:2781: test -s conftest.o
configure:2784: $? = 0
configure:2795: result: yes
configure:2812: checking for gcc option to accept ANSI C
configure:2882: gcc  -c -g -O2  conftest.c >&5
configure:2888: $? = 0
configure:2892: test -z 
			 || test ! -s conftest.err
configure:2895: $? = 0
configure:2898: test -s conftest.o
configure:2901: $? = 0
configure:2919: result: none needed
configure:2937: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'me'
configure:2943: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif
configure:3078: checking dependency style of gcc
configure:3168: result: gcc3
configure:3186: checking for library containing strerror
configure:3216: gcc -o conftest -g -O2   conftest.c  >&5
configure:3222: $? = 0
configure:3226: test -z 
			 || test ! -s conftest.err
configure:3229: $? = 0
configure:3232: test -s conftest
configure:3235: $? = 0
configure:3305: result: none required
configure:3358: checking for gcc
configure:3384: result: gcc
configure:3628: checking for C compiler version
configure:3631: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3634: $? = 0
configure:3636: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:3639: $? = 0
configure:3641: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:3644: $? = 1
configure:3647: checking whether we are using the GNU C compiler
configure:3703: result: yes
configure:3709: checking whether gcc accepts -g
configure:3760: result: yes
configure:3777: checking for gcc option to accept ANSI C
configure:3884: result: none needed
configure:3902: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'me'
configure:3908: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif
configure:4043: checking dependency style of gcc
configure:4133: result: gcc3
configure:4155: checking how to run the C preprocessor
configure:4190: gcc -E  conftest.c
configure:4196: $? = 0
configure:4228: gcc -E  conftest.c
conftest.c:11:28: error: ac_nonexistent.h: No such file or directory
configure:4234: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "avant-window-navigator"
| #define PACKAGE_TARNAME "avant-window-navigator"
| #define PACKAGE_VERSION "0.1.1"
| #define PACKAGE_STRING "avant-window-navigator 0.1.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "avant-window-navigator"
| #define VERSION "0.1.1"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:4273: result: gcc -E
configure:4297: gcc -E  conftest.c
configure:4303: $? = 0
configure:4335: gcc -E  conftest.c
conftest.c:11:28: error: ac_nonexistent.h: No such file or directory
configure:4341: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "avant-window-navigator"
| #define PACKAGE_TARNAME "avant-window-navigator"
| #define PACKAGE_VERSION "0.1.1"
| #define PACKAGE_STRING "avant-window-navigator 0.1.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "avant-window-navigator"
| #define VERSION "0.1.1"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:4385: checking for egrep
configure:4395: result: grep -E
configure:4400: checking for ANSI C header files
configure:4425: gcc -c -g -O2  conftest.c >&5
configure:4431: $? = 0
configure:4435: test -z 
			 || test ! -s conftest.err
configure:4438: $? = 0
configure:4441: test -s conftest.o
configure:4444: $? = 0
configure:4533: gcc -o conftest -g -O2   conftest.c  >&5
conftest.c: In function 'main':
conftest.c:28: warning: incompatible implicit declaration of built-in function 'exit'
configure:4536: $? = 0
configure:4538: ./conftest
configure:4541: $? = 0
configure:4556: result: yes
configure:4644: checking build system type
configure:4662: result: i686-pc-linux-gnu
configure:4670: checking host system type
configure:4684: result: i686-pc-linux-gnu
configure:4692: checking for a sed that does not truncate output
configure:4748: result: /bin/sed
configure:4762: checking for ld used by gcc
configure:4829: result: /usr/bin/ld
configure:4838: checking if the linker (/usr/bin/ld) is GNU ld
configure:4853: result: yes
configure:4858: checking for /usr/bin/ld option to reload object files
configure:4865: result: -r
configure:4883: checking for BSD-compatible nm
configure:4932: result: /usr/bin/nm -B
configure:4936: checking whether ln -s works
configure:4940: result: yes
configure:4947: checking how to recognise dependent libraries
configure:5123: result: pass_all
configure:5368: checking for sys/types.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for sys/stat.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for stdlib.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for string.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for memory.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for strings.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for inttypes.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for stdint.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5368: checking for unistd.h
configure:5384: gcc -c -g -O2  conftest.c >&5
configure:5390: $? = 0
configure:5394: test -z 
			 || test ! -s conftest.err
configure:5397: $? = 0
configure:5400: test -s conftest.o
configure:5403: $? = 0
configure:5414: result: yes
configure:5440: checking dlfcn.h usability
configure:5452: gcc -c -g -O2  conftest.c >&5
configure:5458: $? = 0
configure:5462: test -z 
			 || test ! -s conftest.err
configure:5465: $? = 0
configure:5468: test -s conftest.o
configure:5471: $? = 0
configure:5481: result: yes
configure:5485: checking dlfcn.h presence
configure:5495: gcc -E  conftest.c
configure:5501: $? = 0
configure:5521: result: yes
configure:5556: checking for dlfcn.h
configure:5563: result: yes
configure:5628: checking for g++
configure:5644: found /usr/bin/g++
configure:5654: result: g++
configure:5670: checking for C++ compiler version
configure:5673: g++ --version </dev/null >&5
g++ (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:5676: $? = 0
configure:5678: g++ -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:5681: $? = 0
configure:5683: g++ -V </dev/null >&5
g++: '-V' option must have argument
configure:5686: $? = 1
configure:5689: checking whether we are using the GNU C++ compiler
configure:5713: g++ -c   conftest.cc >&5
configure:5719: $? = 0
configure:5723: test -z 
			 || test ! -s conftest.err
configure:5726: $? = 0
configure:5729: test -s conftest.o
configure:5732: $? = 0
configure:5745: result: yes
configure:5751: checking whether g++ accepts -g
configure:5772: g++ -c -g  conftest.cc >&5
configure:5778: $? = 0
configure:5782: test -z 
			 || test ! -s conftest.err
configure:5785: $? = 0
configure:5788: test -s conftest.o
configure:5791: $? = 0
configure:5802: result: yes
configure:5844: g++ -c -g -O2  conftest.cc >&5
configure:5850: $? = 0
configure:5854: test -z 
			 || test ! -s conftest.err
configure:5857: $? = 0
configure:5860: test -s conftest.o
configure:5863: $? = 0
configure:5889: g++ -c -g -O2  conftest.cc >&5
conftest.cc: In function 'int main()':
conftest.cc:26: error: 'exit' was not declared in this scope
configure:5895: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "avant-window-navigator"
| #define PACKAGE_TARNAME "avant-window-navigator"
| #define PACKAGE_VERSION "0.1.1"
| #define PACKAGE_STRING "avant-window-navigator 0.1.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "avant-window-navigator"
| #define VERSION "0.1.1"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:5844: g++ -c -g -O2  conftest.cc >&5
configure:5850: $? = 0
configure:5854: test -z 
			 || test ! -s conftest.err
configure:5857: $? = 0
configure:5860: test -s conftest.o
configure:5863: $? = 0
configure:5889: g++ -c -g -O2  conftest.cc >&5
configure:5895: $? = 0
configure:5899: test -z 
			 || test ! -s conftest.err
configure:5902: $? = 0
configure:5905: test -s conftest.o
configure:5908: $? = 0
configure:5933: checking dependency style of g++
configure:6023: result: gcc3
configure:6050: checking how to run the C++ preprocessor
configure:6081: g++ -E  conftest.cc
configure:6087: $? = 0
configure:6119: g++ -E  conftest.cc
conftest.cc:25:28: error: ac_nonexistent.h: No such file or directory
configure:6125: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "avant-window-navigator"
| #define PACKAGE_TARNAME "avant-window-navigator"
| #define PACKAGE_VERSION "0.1.1"
| #define PACKAGE_STRING "avant-window-navigator 0.1.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "avant-window-navigator"
| #define VERSION "0.1.1"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:6164: result: g++ -E
configure:6188: g++ -E  conftest.cc
configure:6194: $? = 0
configure:6226: g++ -E  conftest.cc
conftest.cc:25:28: error: ac_nonexistent.h: No such file or directory
configure:6232: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "avant-window-navigator"
| #define PACKAGE_TARNAME "avant-window-navigator"
| #define PACKAGE_VERSION "0.1.1"
| #define PACKAGE_STRING "avant-window-navigator 0.1.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "avant-window-navigator"
| #define VERSION "0.1.1"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:6329: checking for g77
configure:6358: result: no
configure:6329: checking for f77
configure:6358: result: no
configure:6329: checking for xlf
configure:6358: result: no
configure:6329: checking for frt
configure:6358: result: no
configure:6329: checking for pgf77
configure:6358: result: no
configure:6329: checking for fort77
configure:6358: result: no
configure:6329: checking for fl32
configure:6358: result: no
configure:6329: checking for af77
configure:6358: result: no
configure:6329: checking for f90
configure:6358: result: no
configure:6329: checking for xlf90
configure:6358: result: no
configure:6329: checking for pgf90
configure:6358: result: no
configure:6329: checking for epcf90
configure:6358: result: no
configure:6329: checking for f95
configure:6358: result: no
configure:6329: checking for fort
configure:6358: result: no
configure:6329: checking for xlf95
configure:6358: result: no
configure:6329: checking for ifc
configure:6358: result: no
configure:6329: checking for efc
configure:6358: result: no
configure:6329: checking for pgf95
configure:6358: result: no
configure:6329: checking for lf95
configure:6358: result: no
configure:6329: checking for gfortran
configure:6358: result: no
configure:6370: checking for Fortran 77 compiler version
configure:6373:  --version </dev/null >&5
./configure: line 6374: --version: command not found
configure:6376: $? = 127
configure:6378:  -v </dev/null >&5
./configure: line 6379: -v: command not found
configure:6381: $? = 127
configure:6383:  -V </dev/null >&5
./configure: line 6384: -V: command not found
configure:6386: $? = 127
configure:6394: checking whether we are using the GNU Fortran 77 compiler
configure:6408:  -c  conftest.F >&5
./configure: line 6409: -c: command not found
configure:6414: $? = 127
configure: failed program was:
|       program main
| #ifndef __GNUC__
|        choke me
| #endif
| 
|       end
configure:6440: result: no
configure:6446: checking whether  accepts -g
configure:6458:  -c -g conftest.f >&5
./configure: line 6459: -c: command not found
configure:6464: $? = 127
configure: failed program was:
|       program main
| 
|       end
configure:6489: result: no
configure:6519: checking the maximum length of command line arguments
configure:6628: result: 32768
configure:6639: checking command to parse /usr/bin/nm -B output from gcc object
configure:6744: gcc -c -g -O2  conftest.c >&5
configure:6747: $? = 0
configure:6751: /usr/bin/nm -B conftest.o \| sed -n -e 's/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' \> conftest.nm
configure:6754: $? = 0
configure:6806: gcc -o conftest -g -O2   conftest.c conftstm.o >&5
configure:6809: $? = 0
configure:6847: result: ok
configure:6851: checking for objdir
configure:6866: result: .libs
configure:6956: checking for ar
configure:6972: found /usr/bin/ar
configure:6983: result: ar
configure:7036: checking for ranlib
configure:7052: found /usr/bin/ranlib
configure:7063: result: ranlib
configure:7116: checking for strip
configure:7132: found /usr/bin/strip
configure:7143: result: strip
configure:7415: checking if gcc supports -fno-rtti -fno-exceptions
configure:7433: gcc -c -g -O2  -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option "-fno-rtti" is valid for C++/ObjC++ but not for C
configure:7437: $? = 0
configure:7450: result: no
configure:7465: checking for gcc option to produce PIC
configure:7675: result: -fPIC
configure:7683: checking if gcc PIC flag -fPIC works
configure:7701: gcc -c -g -O2  -fPIC -DPIC conftest.c >&5
configure:7705: $? = 0
configure:7718: result: yes
configure:7746: checking if gcc static flag -static works
configure:7774: result: yes
configure:7784: checking if gcc supports -c -o file.o
configure:7805: gcc -c -g -O2  -o out/conftest2.o conftest.c >&5
configure:7809: $? = 0
configure:7831: result: yes
configure:7857: checking whether the gcc linker (/usr/bin/ld) supports shared libraries
configure:8815: result: yes
configure:8836: checking whether -lc should be explicitly linked in
configure:8841: gcc -c -g -O2  conftest.c >&5
configure:8844: $? = 0
configure:8859: gcc -shared conftest.o  -v -Wl,-soname -Wl,conftest -o conftest 2\>\&1 \| grep  -lc  \>/dev/null 2\>\&1
configure:8862: $? = 0
configure:8874: result: no
configure:8882: checking dynamic linker characteristics
configure:9491: result: GNU/Linux ld.so
configure:9500: checking how to hardcode library paths into programs
configure:9525: result: immediate
configure:9539: checking whether stripping libraries is possible
configure:9544: result: yes
configure:10378: checking if libtool supports shared libraries
configure:10380: result: yes
configure:10383: checking whether to build shared libraries
configure:10404: result: yes
configure:10407: checking whether to build static libraries
configure:10411: result: yes
configure:10503: creating libtool
configure:11094: checking for ld used by g++
configure:11161: result: /usr/bin/ld
configure:11170: checking if the linker (/usr/bin/ld) is GNU ld
configure:11185: result: yes
configure:11236: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:12174: result: yes
configure:12192: g++ -c -g -O2  conftest.cpp >&5
configure:12195: $? = 0
configure:12314: checking for g++ option to produce PIC
configure:12588: result: -fPIC
configure:12596: checking if g++ PIC flag -fPIC works
configure:12614: g++ -c -g -O2  -fPIC -DPIC conftest.cpp >&5
configure:12618: $? = 0
configure:12631: result: yes
configure:12659: checking if g++ static flag -static works
configure:12687: result: yes
configure:12697: checking if g++ supports -c -o file.o
configure:12718: g++ -c -g -O2  -o out/conftest2.o conftest.cpp >&5
configure:12722: $? = 0
configure:12744: result: yes
configure:12770: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:12795: result: yes
configure:12862: checking dynamic linker characteristics
configure:13471: result: GNU/Linux ld.so
configure:13480: checking how to hardcode library paths into programs
configure:13505: result: immediate
configure:19734: checking for intltool >= 0.34
configure:19741: result: 0.35.0 found
configure:19797: checking for perl
configure:19815: found /usr/bin/perl
configure:19827: result: /usr/bin/perl
configure:19845: checking for XML::Parser
configure:19848: result: ok
configure:19859: checking for iconv
configure:19877: found /usr/bin/iconv
configure:19890: result: /usr/bin/iconv
configure:19899: checking for msgfmt
configure:19930: result: msgfmt
configure:19939: checking for msgmerge
configure:19970: result: msgmerge
configure:19979: checking for xgettext
configure:20010: result: xgettext
configure:20043: checking locale.h usability
configure:20055: gcc -c -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2  conftest.c >&5
configure:20061: $? = 0
configure:20065: test -z 
			 || test ! -s conftest.err
configure:20068: $? = 0
configure:20071: test -s conftest.o
configure:20074: $? = 0
configure:20084: result: yes
configure:20088: checking locale.h presence
configure:20098: gcc -E  conftest.c
configure:20104: $? = 0
configure:20124: result: yes
configure:20159: checking for locale.h
configure:20166: result: yes
configure:20180: checking for LC_MESSAGES
configure:20201: gcc -o conftest -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2   conftest.c  >&5
configure:20207: $? = 0
configure:20211: test -z 
			 || test ! -s conftest.err
configure:20214: $? = 0
configure:20217: test -s conftest
configure:20220: $? = 0
configure:20232: result: yes
configure:20261: checking libintl.h usability
configure:20273: gcc -c -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2  conftest.c >&5
configure:20279: $? = 0
configure:20283: test -z 
			 || test ! -s conftest.err
configure:20286: $? = 0
configure:20289: test -s conftest.o
configure:20292: $? = 0
configure:20302: result: yes
configure:20306: checking libintl.h presence
configure:20316: gcc -E  conftest.c
configure:20322: $? = 0
configure:20342: result: yes
configure:20377: checking for libintl.h
configure:20384: result: yes
configure:20395: checking for ngettext in libc
configure:20418: gcc -o conftest -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2   conftest.c  >&5
configure:20424: $? = 0
configure:20428: test -z 
			 || test ! -s conftest.err
configure:20431: $? = 0
configure:20434: test -s conftest
configure:20437: $? = 0
configure:20450: result: yes
configure:20454: checking for dgettext in libc
configure:20477: gcc -o conftest -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2   conftest.c  >&5
configure:20483: $? = 0
configure:20487: test -z 
			 || test ! -s conftest.err
configure:20490: $? = 0
configure:20493: test -s conftest
configure:20496: $? = 0
configure:20509: result: yes
configure:20518: checking for bind_textdomain_codeset
configure:20575: gcc -o conftest -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2   conftest.c  >&5
configure:20581: $? = 0
configure:20585: test -z 
			 || test ! -s conftest.err
configure:20588: $? = 0
configure:20591: test -s conftest
configure:20594: $? = 0
configure:20606: result: yes
configure:21116: checking for msgfmt
configure:21146: result: no
configure:21675: checking for pkg-config
configure:21693: found /usr/bin/pkg-config
configure:21705: result: /usr/bin/pkg-config
configure:21720: checking pkg-config is at least version 0.7
configure:21723: result: yes
configure:21741: checking for GLIB - version >= 2.8.0
configure:21860: gcc -o conftest -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     conftest.c -lgobject-2.0 -lglib-2.0    >&5
conftest.c: In function 'main':
conftest.c:41: warning: ignoring return value of 'system', declared with attribute warn_unused_result
configure:21863: $? = 0
configure:21865: ./conftest
configure:21868: $? = 0
configure:21886: result: yes (version 2.12.11)
configure:21985: checking for AWN
configure:21993: $PKG_CONFIG --exists --print-errors " $COMMON_MODULES libwnck-1.0 gconf-2.0"
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gdk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-2.0' found
Package libwnck-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libwnck-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libwnck-1.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
configure:21996: $? = 1
configure:22011: $PKG_CONFIG --exists --print-errors " $COMMON_MODULES libwnck-1.0 gconf-2.0"
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gdk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-2.0' found
Package libwnck-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libwnck-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libwnck-1.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
configure:22014: $? = 1
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found
configure:22052: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_build_alias=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_AWN_CFLAGS_set=
ac_cv_env_AWN_CFLAGS_value=
ac_cv_env_AWN_LIBS_set=
ac_cv_env_AWN_LIBS_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_exeext=
ac_cv_f77_compiler_gnu=no
ac_cv_func_bind_textdomain_codeset=yes
ac_cv_header_dlfcn_h=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_libintl_h=yes
ac_cv_header_locale_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_unistd_h=yes
ac_cv_host=i686-pc-linux-gnu
ac_cv_host_alias=i686-pc-linux-gnu
ac_cv_objext=o
ac_cv_path_INTLTOOL_ICONV=/usr/bin/iconv
ac_cv_path_INTLTOOL_MSGFMT=msgfmt
ac_cv_path_INTLTOOL_MSGMERGE=msgmerge
ac_cv_path_INTLTOOL_PERL=/usr/bin/perl
ac_cv_path_INTLTOOL_XGETTEXT=xgettext
ac_cv_path_MSGFMT=no
ac_cv_path_ac_pt_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_CXXCPP='g++ -E'
ac_cv_prog_ac_ct_AR=ar
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_ac_ct_STRIP=strip
ac_cv_prog_cc_g=yes
ac_cv_prog_cc_stdc=
ac_cv_prog_cxx_g=yes
ac_cv_prog_egrep='grep -E'
ac_cv_prog_f77_g=no
ac_cv_prog_make_make_set=yes
ac_cv_search_strerror='none required'
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_CXX_dependencies_compiler_type=gcc3
am_cv_prog_tar_ustar=gnutar
am_cv_val_LC_MESSAGES=yes
gt_cv_func_dgettext_libc=yes
gt_cv_func_dgettext_libintl=no
gt_cv_func_ngettext_libc=yes
gt_cv_have_gettext=no
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file=
lt_cv_ld_reload_flag=-r
lt_cv_objdir=.libs
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_LDCXX=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_SED=/bin/sed
lt_cv_prog_compiler_c_o=yes
lt_cv_prog_compiler_c_o_CXX=yes
lt_cv_prog_compiler_rtti_exceptions=no
lt_cv_prog_gnu_ld=yes
lt_cv_prog_gnu_ldcxx=yes
lt_cv_sys_global_symbol_pipe='sed -n -e '\''s/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p'\'''
lt_cv_sys_global_symbol_to_c_name_address='sed -n -e '\''s/^: \([^ ]*\) $/  {\"\1\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \([^ ]*\) \([^ ]*\)$/  {"\2", (lt_ptr) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_cdecl='sed -n -e '\''s/^. .* \(.*\)$/extern int \1;/p'\'''
lt_cv_sys_max_cmd_len=32768
lt_lt_cv_prog_compiler_c_o='"yes"'
lt_lt_cv_prog_compiler_c_o_CXX='"yes"'
lt_lt_cv_sys_global_symbol_pipe='"sed -n -e '\''s/^.*[ 	]\\([ABCDGIRSTW][ABCDGIRSTW]*\\)[ 	][ 	]*\\([_A-Za-z][_A-Za-z0-9]*\\)\$/\\1 \\2 \\2/p'\''"'
lt_lt_cv_sys_global_symbol_to_c_name_address='"sed -n -e '\''s/^: \\([^ ]*\\) \$/  {\\\"\\1\\\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \\([^ ]*\\) \\([^ ]*\\)\$/  {\"\\2\", (lt_ptr) \\&\\2},/p'\''"'
lt_lt_cv_sys_global_symbol_to_cdecl='"sed -n -e '\''s/^. .* \\(.*\\)\$/extern int \\1;/p'\''"'

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/alex/Desktop/avant-window-navigator-0.1.1/missing --run aclocal-1.9'
ACLOCAL_AMFLAGS='${ACLOCAL_FLAGS}'
ALL_LINGUAS='en_GB'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/alex/Desktop/avant-window-navigator-0.1.1/missing --run tar'
AR='ar'
AUTOCONF='${SHELL} /home/alex/Desktop/avant-window-navigator-0.1.1/missing --run autoconf'
AUTOHEADER='${SHELL} /home/alex/Desktop/avant-window-navigator-0.1.1/missing --run autoheader'
AUTOMAKE='${SHELL} /home/alex/Desktop/avant-window-navigator-0.1.1/missing --run automake-1.9'
AWK='mawk'
AWN_CFLAGS=''
AWN_LIBS=''
CATALOGS=''
CATOBJEXT='NONE'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2'
CPP='gcc -E'
CPPFLAGS=''
CXX='g++'
CXXCPP='g++ -E'
CXXDEPMODE='depmode=gcc3'
CXXFLAGS='-g -O2'
CYGPATH_W='echo'
DATADIRNAME=''
DEFS=''
DEPDIR='.deps'
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='grep -E'
EXEEXT=''
F77=''
FFLAGS=''
GCONFTOOL=''
GCONF_SCHEMAS_INSTALL_FALSE=''
GCONF_SCHEMAS_INSTALL_TRUE=''
GCONF_SCHEMA_CONFIG_SOURCE=''
GCONF_SCHEMA_FILE_DIR=''
GETTEXT_PACKAGE='avant-window-navigator'
GLIB_CFLAGS='-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  '
GLIB_GENMARSHAL='glib-genmarshal'
GLIB_LIBS='-lgobject-2.0 -lglib-2.0  '
GLIB_MKENUMS='glib-mkenums'
GMOFILES=' en_GB.gmo'
GMSGFMT=''
GOBJECT_QUERY='gobject-query'
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
INSTOBJEXT=''
INTLLIBS=''
INTLTOOL_CAVES_RULE='%.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DESKTOP_RULE='%.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DIRECTORY_RULE='%.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_EXTRACT='$(top_builddir)/intltool-extract'
INTLTOOL_ICONV='/usr/bin/iconv'
INTLTOOL_KBD_RULE='%.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -m -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_KEYS_RULE='%.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -k -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_MERGE='$(top_builddir)/intltool-merge'
INTLTOOL_MSGFMT='msgfmt'
INTLTOOL_MSGMERGE='msgmerge'
INTLTOOL_OAF_RULE='%.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -p $(top_srcdir)/po $< $@'
INTLTOOL_PERL='/usr/bin/perl'
INTLTOOL_PONG_RULE='%.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_PROP_RULE='%.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SCHEMAS_RULE='%.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVER_RULE='%.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVICE_RULE='%.service: %.service.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SHEET_RULE='%.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SOUNDLIST_RULE='%.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_THEME_RULE='%.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UI_RULE='%.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UPDATE='$(top_builddir)/intltool-update'
INTLTOOL_XAM_RULE='%.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_XGETTEXT='xgettext'
INTLTOOL_XML_NOMERGE_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@'
INTLTOOL_XML_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBTOOL='$(SHELL) $(top_builddir)/libtool'
LN_S='ln -s'
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /home/alex/Desktop/avant-window-navigator-0.1.1/missing --run makeinfo'
MKINSTALLDIRS='./mkinstalldirs'
MSGFMT='no'
OBJEXT='o'
PACKAGE='avant-window-navigator'
PACKAGE_BUGREPORT=''
PACKAGE_NAME='avant-window-navigator'
PACKAGE_STRING='avant-window-navigator 0.1.1'
PACKAGE_TARNAME='avant-window-navigator'
PACKAGE_VERSION='0.1.1'
PATH_SEPARATOR=':'
PKG_CONFIG='/usr/bin/pkg-config'
POFILES=' en_GB.po'
POSUB='po'
PO_IN_DATADIR_FALSE=''
PO_IN_DATADIR_TRUE=''
RANLIB='ranlib'
SED='/bin/sed'
SET_MAKE=''
SHELL='/bin/bash'
STRIP='strip'
USE_NLS='yes'
VERSION='0.1.1'
XGETTEXT=':'
ac_ct_AR='ar'
ac_ct_CC='gcc'
ac_ct_CXX='g++'
ac_ct_F77=''
ac_ct_RANLIB='ranlib'
ac_ct_STRIP='strip'
ac_pt_PKG_CONFIG='/usr/bin/pkg-config'
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE='#'
am__fastdepCXX_TRUE=''
am__include='include'
am__leading_dot='.'
am__quote=''
am__tar='tar --format=ustar -chf - "$$tardir"'
am__untar='tar -xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${prefix}/share'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/alex/Desktop/avant-window-navigator-0.1.1/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
mkdir_p='mkdir -p --'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
slicelocaledir='${prefix}/${DATADIRNAME}/locale'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define GETTEXT_PACKAGE "avant-window-navigator"
#define HAVE_BIND_TEXTDOMAIN_CODESET 1
#define HAVE_DLFCN_H 1
#define HAVE_GETTEXT 1
#define HAVE_INTTYPES_H 1
#define HAVE_LC_MESSAGES 1
#define HAVE_LOCALE_H 1
#define HAVE_MEMORY_H 1
#define HAVE_STDINT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRINGS_H 1
#define HAVE_STRING_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_UNISTD_H 1
#define PACKAGE "avant-window-navigator"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME "avant-window-navigator"
#define PACKAGE_STRING "avant-window-navigator 0.1.1"
#define PACKAGE_TARNAME "avant-window-navigator"
#define PACKAGE_VERSION "0.1.1"
#define STDC_HEADERS 1
#define VERSION "0.1.1"
#endif
#ifdef __cplusplus
extern "C" void std::exit (int) throw (); using std::exit;

configure: exit 1

Any help in resolving this matter would be greatly appreciated!!!

-Alex

---

### Post by Steveway on 2007-09-02
There are repositories for the avant-window-navigator.
You don't need to compile it.
There are .deb files for most apps, just tell us what you want or better stick to Synaptic and Google.

---

### Post by Vadi on 2007-09-02
I'll second that post, don't try and compile things yourself. See if you can just add a repository and execute some sudo install ... command as provided in the instructions, or install a .deb package, or go to getdeb.net to find one.

As for AWN, search on forums - there's an easy howto that uses the repositiroes to install it somewhere.

---

### Post by aoc153 on 2007-09-02
Thanks alot guys:)

---

