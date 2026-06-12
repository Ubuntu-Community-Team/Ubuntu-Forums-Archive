---
title: "How to install veriwell under 10.04?"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by irfan_s on 2011-03-31
Hi all,

I am trying to install the veriwell 2.8.7: [http://sourceforge.net/projects/veriwell/](http://sourceforge.net/projects/veriwell/)

when I do **./configure** I get this:

```
irfan@irfan-laptop:~/Desktop/veriwell-2.8.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking use 32 bit compile... no
checking enable lxt support... yes
checking enable lxt2 support... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for help2man... /usr/bin/help2man
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... (cached) ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gperf... gperf
checking for bison... bison
checking for gzwrite in -lz... no
checking for BZ2_bzwrite in -lbz2... no
checking for a readline compatible library... no
checking for ANSI C header files... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for memory.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether byte ordering is bigendian... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for memmove... yes
checking for memset... yes
checking for pow... no
checking for strchr... yes
checking for strdup... yes
checking for strrchr... yes
checking for vfscanf in stdio.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating replace/Makefile
config.status: creating replace/libz/Makefile
config.status: creating replace/libbz2/Makefile
config.status: creating src/Makefile
config.status: creating lxt/Makefile
config.status: creating doc/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```ON **make** the output is:

```
irfan@irfan-laptop:~/Desktop/veriwell-2.8.7$ make
make  all-recursive
make[1]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7'
Making all in replace
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
Making all in libz
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libz'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libz'
Making all in libbz2
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libbz2'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libbz2'
Making all in .
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
Making all in lxt
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/lxt'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/lxt'
Making all in src
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/src'
echo '#define BINDIR "/usr/local/bin"' >build.h
echo '#define LIBDIR "/usr/local/lib"' >>build.h
echo '#define INCLUDEDIR "/usr/local/include"' >>build.h
echo '#define CFLAGS "-g -O2"' >>build.h
echo '#define LDFLAGS ""' >>build.h
echo '#define LIBS "  "' >>build.h
make  all-am
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT veriwell.lo -MD -MP -MF .deps/veriwell.Tpo -c -o veriwell.lo veriwell.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT veriwell.lo -MD -MP -MF .deps/veriwell.Tpo -c veriwell.cc  -fPIC -DPIC -o .libs/veriwell.o
In file included from veriwell.cc:41:
glue.h: In member function 'int File::fscanf(char*, ...)':
glue.h:127: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: At global scope:
veriwell.cc:62: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void init()':
veriwell.cc:120: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:140: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:140: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void error_with_file_and_line(char*, lineno_t, char*, char*, char*)':
veriwell.cc:190: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:193: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:195: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:198: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:200: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void warning_with_file_and_line(char*, lineno_t, char*, char*, char*)':
veriwell.cc:225: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:227: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:229: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:231: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void sorry_with_file_and_line(char*, lineno_t, char*, char*, char*)':
veriwell.cc:256: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:258: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:260: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:262: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'char* xmalloc(unsigned int)':
veriwell.cc:304: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'char* xrealloc(char*, int)':
veriwell.cc:315: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'int test_file(char*)':
veriwell.cc:339: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void Cmdline(int, char**)':
veriwell.cc:361: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:366: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:371: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:376: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:391: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:393: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:398: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:415: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:417: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:422: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:436: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:440: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:441: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:446: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:451: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:457: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:476: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:480: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:486: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:490: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:500: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:502: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:507: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:509: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:513: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void process_cmdline(char*)':
veriwell.cc:547: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:561: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:562: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:595: warning: format not a string literal and no format arguments
veriwell.cc: In function 'int moreinput(char*)':
veriwell.cc:763: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:764: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void print_info()':
veriwell.cc:918: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:920: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:922: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:924: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:929: warning: deprecated conversion from string constant to 'char*'
veriwell.cc: In function 'void finish()':
veriwell.cc:935: warning: deprecated conversion from string constant to 'char*'
veriwell.cc:936: warning: deprecated conversion from string constant to 'char*'
 g++ -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT veriwell.lo -MD -MP -MF .deps/veriwell.Tpo -c veriwell.cc -o veriwell.o >/dev/null 2>&1
mv -f .deps/veriwell.Tpo .deps/veriwell.Plo
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2 -version-info 0:0:0  -o libveriwell.la -rpath /usr/local/lib parse.lo sdfparse.lo sdfcpars.lo multdiv.lo print.lo usertask.lo flags.lo store.lo nsched.lo verisys.lo check.lo gates.lo schedule.lo strobe.lo glue.lo obstack.lo scope.lo timescal.lo systask.lo copy.lo veriwell.lo pass2.lo sdf.lo sdfclex.lo decl.lo io.lo pass3.lo trace.lo dumpvar.lo lex.lo pli.lo tree.lo sdflex.lo eval.lo macro.lo udp.lo exec.lo specify.lo plihacks.lo random.lo ../lxt/liblxt.la ../replace/libreplace.la 
rm -fr  .libs/libveriwell.a .libs/libveriwell.la .libs/libveriwell.lai .libs/libveriwell.so .libs/libveriwell.so.0 .libs/libveriwell.so.0.0.0
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.4.3/crtbeginS.o  .libs/parse.o .libs/sdfparse.o .libs/sdfcpars.o .libs/multdiv.o .libs/print.o .libs/usertask.o .libs/flags.o .libs/store.o .libs/nsched.o .libs/verisys.o .libs/check.o .libs/gates.o .libs/schedule.o .libs/strobe.o .libs/glue.o .libs/obstack.o .libs/scope.o .libs/timescal.o .libs/systask.o .libs/copy.o .libs/veriwell.o .libs/pass2.o .libs/sdf.o .libs/sdfclex.o .libs/decl.o .libs/io.o .libs/pass3.o .libs/trace.o .libs/dumpvar.o .libs/lex.o .libs/pli.o .libs/tree.o .libs/sdflex.o .libs/eval.o .libs/macro.o .libs/udp.o .libs/exec.o .libs/specify.o .libs/plihacks.o .libs/random.o -Wl,--whole-archive ../lxt/.libs/liblxt.a ../replace/.libs/libreplace.a -Wl,--no-whole-archive  -L/usr/lib/gcc/i486-linux-gnu/4.4.3 -L/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.4.3/../../.. -L/usr/lib/i486-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.4.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crtn.o  -Wl,-soname -Wl,libveriwell.so.0 -o .libs/libveriwell.so.0.0.0
(cd .libs && rm -f libveriwell.so.0 && ln -s libveriwell.so.0.0.0 libveriwell.so.0)
(cd .libs && rm -f libveriwell.so && ln -s libveriwell.so.0.0.0 libveriwell.so)
rm -fr .libs/libveriwell.lax
mkdir .libs/libveriwell.lax
rm -fr .libs/libveriwell.lax/liblxt.a
mkdir .libs/libveriwell.lax/liblxt.a
(cd .libs/libveriwell.lax/liblxt.a && ar x /home/irfan/Desktop/veriwell-2.8.7/src/../lxt/.libs/liblxt.a)
rm -fr .libs/libveriwell.lax/libreplace.a
mkdir .libs/libveriwell.lax/libreplace.a
(cd .libs/libveriwell.lax/libreplace.a && ar x /home/irfan/Desktop/veriwell-2.8.7/src/../replace/.libs/libreplace.a)
ar cru .libs/libveriwell.a  parse.o sdfparse.o sdfcpars.o multdiv.o print.o usertask.o flags.o store.o nsched.o verisys.o check.o gates.o schedule.o strobe.o glue.o obstack.o scope.o timescal.o systask.o copy.o veriwell.o pass2.o sdf.o sdfclex.o decl.o io.o pass3.o trace.o dumpvar.o lex.o pli.o tree.o sdflex.o eval.o macro.o udp.o exec.o specify.o plihacks.o random.o  .libs/libveriwell.lax/liblxt.a/lxt.o .libs/libveriwell.lax/liblxt.a/lxt2_write.o .libs/libveriwell.lax/liblxt.a/lxt_write.o .libs/libveriwell.lax/liblxt.a/lxt2.o  .libs/libveriwell.lax/libreplace.a/crc32.o .libs/libveriwell.lax/libreplace.a/zutil.o .libs/libveriwell.lax/libreplace.a/gzio.o .libs/libveriwell.lax/libreplace.a/blocksort.o .libs/libveriwell.lax/libreplace.a/adler32.o .libs/libveriwell.lax/libreplace.a/deflate.o .libs/libveriwell.lax/libreplace.a/bzdecompress.o .libs/libveriwell.lax/libreplace.a/huffman.o .libs/libveriwell.lax/libreplace.a/bzlib.o .libs/libveriwell.lax/libreplace.a/readline.o .libs/libveriwell.lax/libreplace.a/randtable.o .libs/libveriwell.lax/libreplace.a/inflate.o .libs/libveriwell.lax/libreplace.a/inftrees.o .libs/libveriwell.lax/libreplace.a/uncompr.o .libs/libveriwell.lax/libreplace.a/bzcompress.o .libs/libveriwell.lax/libreplace.a/crctable.o .libs/libveriwell.lax/libreplace.a/trees.o .libs/libveriwell.lax/libreplace.a/inffast.o .libs/libveriwell.lax/libreplace.a/infback.o .libs/libveriwell.lax/libreplace.a/compress.o 
ranlib .libs/libveriwell.a
rm -fr .libs/libveriwell.lax
creating libveriwell.la
(cd .libs && rm -f libveriwell.la && ln -s ../libveriwell.la libveriwell.la)
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2   -o veriwell defaultveriuser.o  libveriwell.la   
g++ -g -O2 -o .libs/veriwell defaultveriuser.o  ./.libs/libveriwell.so
creating veriwell
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/src'
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/src'
Making all in doc
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/doc'
Making all in .
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7'
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7'
make[1]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7'

```The **make install** is:

```
irfan@irfan-laptop:~/Desktop/veriwell-2.8.7$ make install
Making install in replace
make[1]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
Making install in libz
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libz'
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libz'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libz'
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libz'
Making install in libbz2
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libbz2'
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libbz2'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libbz2'
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace/libbz2'
Making install in .
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
make[1]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/replace'
Making install in lxt
make[1]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/lxt'
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/lxt'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/lxt'
make[1]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/lxt'
Making install in src
make[1]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/src'
make  install-am
make[2]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/src'
make[3]: Entering directory `/home/irfan/Desktop/veriwell-2.8.7/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libveriwell.la' '/usr/local/lib/libveriwell.la'
/usr/bin/install -c .libs/libveriwell.so.0.0.0 /usr/local/lib/libveriwell.so.0.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libveriwell.so.0.0.0': Permission denied
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/irfan/Desktop/veriwell-2.8.7/src'
make: *** [install-recursive] Error 1

```Does anybody have an idea where the problem might be? 

Thank you in advance.

---

### Post by irfan_s on 2011-03-31
Ups. I forgot the root. :popcorn:

---

### Post by Enigmapond on 2011-03-31
[http://tugll.tugraz.at/rotut2010/weblog/10198.html](http://tugll.tugraz.at/rotut2010/weblog/10198.html) There are deb files here that may be of some assistance. It's states 10.10 but I think they are probably for all distros. Und es ist auf Deutsch..:)

---

### Post by irfan_s on 2011-03-31
Actually thats from my university, lol. :) Thanks

---

