---
title: "Error with &quot;make&quot;"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by James_Jang on 2014-07-25
[COLOR=#000000][FONT=monospace]I m trying to install soundtouch package but I m having some problems[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]I m following their instruction on how to compile soundtouch after unzipping the file.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]It tells me to [/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]./configure  -[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Configures the SoundTouch package for the local environment.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]make         -[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Builds the SoundTouch library & SoundStretch utility.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]make install -[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Installs the SoundTouch & BPM libraries to /usr/local/lib and SoundStretch utility to /usr/local/bin. Please notice that 'root' privileges may be required to install the binaries to the destination locations.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]I did the first step but when I run make, it gives me errors.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]james@Bum-Ho:~/pitch shifter/soundtouch$ make[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] cd . && automake-1.10 --foreign [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/bin/bash: line 4: automake-1.10: command not found[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]make: *** [Makefile.in] Error 1[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]What could be the problem? I looked up to see if I had automake installed and I did so I dont understand what is going on.[/FONT][/COLOR]

---

### Post by steeldriver on 2014-07-25
Hello and welcome to the forums

Did you make a careful note of any errors during the ./configure stage? Did it complain about automake-1.10 then?

FYI automake-1.10 is a different thing from automake - in particular

```

$ apt-cache show automake1.10
Package: automake1.10
Priority: optional
Section: devel
.
.
.
Description-en: A tool for generating GNU Standards-compliant Makefiles
 Automake is a tool for automatically generating `Makefile.in's from
 files called `Makefile.am'.
 .
 The goal of Automake is to remove the burden of Makefile maintenance
 from the back of the individual GNU maintainer (and put it on the back
 of the Automake maintainer).
 .
 The `Makefile.am' is basically a series of `make' macro definitions
 (with rules being thrown in occasionally).  The generated
 `Makefile.in's are compliant with the GNU Makefile standards.
 .
[B] Automake 1.10 fails to work in a number of situations that Automake
 1.4, 1.6, 1.7, 1.8 and 1.9 did, so has been renamed so that the
 previous version can continue to be made available.[/B]
Homepage: http://www.gnu.org/software/automake/
Description-md5: 6f497af7609daf9f483b9ba343a4ebe4
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m

```

---

### Post by James_Jang on 2014-07-25
I dont think it complained.

This was the message I received when I ran ./configure

james@Bum-Ho:~/pitch shifter/soundtouch$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/james/pitch: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgfortran... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking for nagfor... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
****** Float sample type enabled ******
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking return type of signal handlers... void
checking for sqrt in -lm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating source/Makefile
config.status: creating source/SoundTouch/Makefile
config.status: creating source/SoundStretch/Makefile
config.status: creating include/Makefile
config.status: creating soundtouch-1.4.pc
config.status: creating include/soundtouch_config.h
config.status: include/soundtouch_config.h is unchanged
config.status: executing depfiles commands

---

