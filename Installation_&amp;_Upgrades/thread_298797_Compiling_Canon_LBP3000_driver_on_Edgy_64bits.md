---
title: "Compiling Canon LBP3000 driver on Edgy 64bits"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by kris969 on 2006-11-13
Today sources cndrvcups-capt-1.30 et cndrvcups-common-1.30 are available on japan website. Is there anybody who tried to compile these on an Ubuntu AMD64.
On my side I'm trying to do it, as there are other interesting solutions proposed on English and French forum, I still believe that it could be interesting for many people to have a complete installation guide using Canon's driver sources.

I did, by the past, a lot of software development (it was my job) but not on linux. So now I'm trying to do this and I get some problem on witch I should appreciate help for any people who well know how to do.

After having uncompressed the files, I do (following le readme file) a **make gen** command.
Step by step I have added the requested packages (using synaptic) and from know the process goes quite long but end whith this messages :

```

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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking for vprintf... yes
checking for _doprnt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Now type `make' to compile canoncapt
make[1]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
cd . && /bin/bash /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver/missing --run autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
touch ./config.h.in
make  all-am
make[2]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
make[2]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
make[1]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for memset... yes
checking for strchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Now type `make' to compile backend
make[1]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
cd . && /bin/bash /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend/missing --run autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
touch ./config.h.in
make  all-am
make[2]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
gcc -O2 -Wall -fPIC -g -O2   -o ccp  ccp.o -lcups 
/usr/bin/ld: ne peut trouver -lcups
collect2: ld returned 1 exit status
make[2]: *** [ccp] Erreur 1
make[2]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
make[1]: *** [all] Erreur 2
make[1]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
make: *** [gen] Erreur 1
kris@kris-desktop:~/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30$ make gen
for dir in driver backend pstocapt pstocapt2 statusui ppd; do (cd $dir; ./autogen.sh; make $target) || exit 1; done
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running libtoolize...
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking for vprintf... yes
checking for _doprnt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Now type `make' to compile canoncapt
make[1]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
cd . && /bin/bash /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver/missing --run autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
touch ./config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-am
make[2]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
make[2]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
make[1]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/driver »
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for memset... yes
checking for strchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Now type `make' to compile backend
make[1]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
cd . && /bin/bash /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend/missing --run autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
touch ./config.h.in
make  all-am
make[2]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
gcc -O2 -Wall -fPIC -g -O2   -o ccp  ccp.o -lcups 
/usr/bin/ld: ne peut trouver -lcups
collect2: ld returned 1 exit status
make[2]: *** [ccp] Erreur 1
make[2]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
make[1]: *** [all] Erreur 2
make[1]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/backend »
make: *** [gen] Erreur 1
kris@kris-desktop:~/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30$

```


I don't kown what to do know as I don't understand what's 
**/usr/bin/ld: ne peut trouver -lcups** that is can't find -lcups !

Who can help me on this ?

thanks

Kris

---

### Post by kris969 on 2006-11-13
Ok, I went around this problem on downloading the cups library sources, compile and install it. Thanks to the French guy who gave me this idea.

Now the next problem his ... here :
```

checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for dup2... yes
checking for memset... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating filter/Makefile
config.status: creating config.h
config.status: executing depfiles commands
Now type `make' to compile pstocapt
make[1]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/pstocapt »
make  all-recursive
make[2]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/pstocapt »
Making all in filter
make[3]: entrant dans le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/pstocapt/filter »
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -O2 -Wall -fPIC -g -O2 -MT pstocapt.o -MD -MP -MF ".deps/pstocapt.Tpo" \
          -c -o pstocapt.o `test -f 'pstocapt.c' || echo './'`pstocapt.c; \
        then mv -f ".deps/pstocapt.Tpo" ".deps/pstocapt.Po"; \
        else rm -f ".deps/pstocapt.Tpo"; exit 1; \
        fi
pstocapt.c: In function ‘get_ps_params’:
pstocapt.c:396: warning: pointer targets in passing argument 1 of ‘buflist_new’ differ in signedness
pstocapt.c:441: warning: value computed is not used
pstocapt.c:475: warning: pointer targets in passing argument 1 of ‘buflist_new’ differ in signedness
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -O2 -Wall -fPIC -g -O2 -MT paramlist.o -MD -MP -MF ".deps/paramlist.Tpo" \
          -c -o paramlist.o `test -f 'paramlist.c' || echo './'`paramlist.c; \
        then mv -f ".deps/paramlist.Tpo" ".deps/paramlist.Po"; \
        else rm -f ".deps/paramlist.Tpo"; exit 1; \
        fi
gcc -O2 -Wall -fPIC -g -O2   -o pstocapt  pstocapt.o paramlist.o -lbuftool -lcups  -lcups 
/usr/bin/ld: escamotage incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libbuftool.a lors de la recherche de -lbuftool
/usr/bin/ld: escamotage incompatible /usr/lib/../lib64/libbuftool.a lors de la recherche de -lbuftool
/usr/bin/ld: escamotage incompatible /usr/bin/../lib/libbuftool.a lors de la recherche de -lbuftool
/usr/bin/ld: escamotage incompatible /usr/lib64/libbuftool.a lors de la recherche de -lbuftool
/usr/bin/ld: escamotage incompatible /usr/lib/libbuftool.a lors de la recherche de -lbuftool
/usr/bin/ld: ne peut trouver -lbuftool
collect2: ld returned 1 exit status
make[3]: *** [pstocapt] Erreur 1
make[3]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/pstocapt/filter »
make[2]: *** [all-recursive] Erreur 1
make[2]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/pstocapt »
make[1]: *** [all] Erreur 2
make[1]: quittant le répertoire « /home/kris/Desktop/Canon_LBP3000/Source/capt/cndrvcups-capt-1.30/pstocapt »
make: *** [gen] Erreur 1

```

I know I haven't installed the lib buftool that is I don't find it anywhere. A search on Google don't give me enough information !

Is there anyone here with **THE GOOD IDEA** !!!

---

