---
title: "Problems installing 'Sound Scape Renderer'"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by tgriffiths42 on 2011-02-19
Hi everyone,

I have, today, installed ubuntu, as I require it to install a software which has been designed for an area of my research (Wave Field Synthesis).

I have downloaded the (reliable) source information from the developer's website ([http://www.tu-berlin.de/?id=ssr](http://www.tu-berlin.de/?id=ssr)) [source location: [https://dev.qu.tu-berlin.de/attachments/download/78/ssr-0.3.0.tar.gz]](https://dev.qu.tu-berlin.de/attachments/download/78/ssr-0.3.0.tar.gz])

I then unpacked the folder with use of 'tar xvfz', changed the location of the directory to said folder, and attempted to './configure'.  This hasn't been completing successfully, however.

To begin with, I didn't have any compilers installed, etc, so I installed some obvious ones, but must still be missing applications which are required.  Does anyone have any more clue than I do as to what I am missing, to be able to complete the installation?

Any guidance that could be offered would be very much appreciated.  I haven't used ubuntu before, so I will make sure I get my head around it soon - I just haven't the time at the moment, as I need this software urgently for a further bit of research.

The terminal report is linked below.

Many thanks,
T.Griffiths.


-------------------------------------------------------------------------------------------------------------------

t-griffiths@ubuntu:~$ cd /home/t-griffiths/ssr-0.3.0
t-griffiths@ubuntu:~/ssr-0.3.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... yes
checking for FFTW... no
configure: WARNING: *** FFTW3 not found
checking for JACK... yes
checking for LIBXML... yes
checking ecasoundc.h usability... no
checking ecasoundc.h presence... no
checking for ecasoundc.h... no
checking for eci_init in -lecasoundc... no
configure: WARNING: *** libecasoundc not found
checking whether we can compile MMX code... yes
checking whether we can compile SSE code... yes
checking for QT... no
checking GL/glut.h usability... no
checking GL/glut.h presence... no
checking for GL/glut.h... no
checking for library containing glutInit... no
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking for library containing gluNewQuadric... no
Searching for versioned Boost include directory.....not found
checking boost/asio.hpp usability... no
checking boost/asio.hpp presence... no
checking for boost/asio.hpp... no
configure: WARNING: *** Boost.Asio Headers not found
checking for Boost.System library... no
checking for Boost.Threads library... no
checking various header files for Polhemus Fastrak support... see below
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking Polhemus Fastrak support... yes
checking isense.h usability... no
checking isense.h presence... no
checking for isense.h... no
checking types.h usability... no
checking types.h presence... no
checking for types.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating data/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

SoundScape Renderer (SSR) 0.3.0:

| Found JACK library.................................... : true
| Found ecasound library................................ : false
| Found FFTW3 library................................... : false
| Found libxml2 library................................. : true
| Found libsndfile...................................... : true
|
| Build with InterSense tracker support................. : no
| Build with Polhemus Fastrak support................... : yes
| Build with IP interface support....................... : no
| Build with GUI ....................................... : no
|
| Enable debugging ..................................... : no
| Enable optimizations ................................. : yes
|
| Install prefix........................................ : /usr/local

Compiler optimization flags: -O3 -fomit-frame-pointer -ffast-math -funroll-loops -march=i686 -msse -mfpmath=sse
t-griffiths@ubuntu:~/ssr-0.3.0$

---

### Post by tgriffiths42 on 2011-02-19
[Update after some fault-finding...]

-----------------------------------------------------------------------------------------------

t-griffiths@ubuntu:~$ cd /home/t-griffiths/ssr-0.3.0
t-griffiths@ubuntu:~/ssr-0.3.0$ ls
aclocal.m4  config.status  data              libtool      NEWS
AUTHORS     configure      doc               Makefile     python_client
autotools   configure.ac   hrirs_fabian.wav  Makefile.am  README
config.log  COPYING        INSTALL           Makefile.in  src
t-griffiths@ubuntu:~/ssr-0.3.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... yes
checking for FFTW... yes
checking for JACK... yes
checking for LIBXML... yes
checking ecasoundc.h usability... yes
checking ecasoundc.h presence... yes
checking for ecasoundc.h... yes
checking for eci_init in -lecasoundc... yes
checking whether we can compile MMX code... yes
checking whether we can compile SSE code... yes
checking for QT... yes
checking GL/glut.h usability... no
checking GL/glut.h presence... no
checking for GL/glut.h... no
checking for library containing glutInit... no
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking for library containing gluNewQuadric... -lGLU
checking boost/asio.hpp usability... yes
checking boost/asio.hpp presence... yes
checking for boost/asio.hpp... yes
checking for Boost.System library... no
checking for Boost.Threads library... -lboost_thread-mt
checking various header files for Polhemus Fastrak support... see below
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking Polhemus Fastrak support... yes
checking isense.h usability... no
checking isense.h presence... no
checking for isense.h... no
checking types.h usability... no
checking types.h presence... no
checking for types.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating data/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

SoundScape Renderer (SSR) 0.3.0:

| Found JACK library.................................... : true
| Found ecasound library................................ : true
| Found FFTW3 library................................... : true
| Found libxml2 library................................. : true
| Found libsndfile...................................... : true
|
| Build with InterSense tracker support................. : no
| Build with Polhemus Fastrak support................... : yes
| Build with IP interface support....................... : no
| Build with GUI ....................................... : no
|
| Enable debugging ..................................... : no
| Enable optimizations ................................. : yes
|
| Install prefix........................................ : /usr/local

Compiler optimization flags: -O3 -fomit-frame-pointer -ffast-math -funroll-loops -march=i686 -msse -mfpmath=sse

---

