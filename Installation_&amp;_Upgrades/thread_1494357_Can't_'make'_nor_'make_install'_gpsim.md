---
title: "Can't 'make' nor 'make install' gpsim"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by LePresident on 2010-05-26
Well, as the title says, I can't install gpsim.  I got the .tar.gz and I've already exctracted the file, but when I try to 'make' the file, I got a series of errors.

What's happening? 

Here is what I get when I try to 'make' the file:

```
root@votrecauchemar:~/Escritorio/gpsim-0.24.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
enabling gui support
disabling gpsim socket interface
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking popt.h usability... yes
checking popt.h presence... yes
checking for popt.h... yes
checking for pkg-config... /usr/bin/pkg-config
linking with gtk-2.20.0
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for main in -lpopt... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking return type of signal handlers... void
checking for working alloca.h... yes
checking for alloca... yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for working strtod... yes
checking for floor... yes
checking for gethostbyname... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for memset... yes
checking for pow... yes
checking for select... yes
checking for socket... yes
checking for sqrt... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strndup... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtoul... yes
checking size of long... 4
configure: creating ./config.status
config.status: creating Makefile
config.status: creating cli/Makefile
config.status: creating doc/Makefile
config.status: creating examples/Makefile
config.status: creating examples/modules/Makefile
config.status: creating examples/projects/Makefile
config.status: creating eXdbm/Makefile
config.status: creating gpsim/Makefile
config.status: creating gui/Makefile
config.status: creating modules/Makefile
config.status: creating regression/Makefile
config.status: creating src/Makefile
config.status: creating src/dspic/Makefile
config.status: creating xpms/Makefile
config.status: creating gpsim.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


gpsim-0.24.0 is now configured for 

  Build:                i686-pc-linux-gnu
  Host:                 i686-pc-linux-gnu
  Source directory:     .
  Installation prefix:  /usr/local
  C compiler:           gcc  -g -O2 -Wall
  C++ compiler:         g++  -g -O2 -Wall

  gui:                  yes
  Socket interface:     no


root@votrecauchemar:~/Escritorio/gpsim-0.24.0# make
make  all-recursive
make[1]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0'
Making all in eXdbm
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
Making all in src
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making all in dspic
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: No se hace nada para `all'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[3]: No se hace nada para `all-am'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making all in cli
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c -o input.lo input.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.cc  -fPIC -DPIC -o .libs/input.o
input.cc:86:31: error: readline/readline.h: No existe el fichero ó directorio
input.cc:87:30: error: readline/history.h: No existe el fichero ó directorio
input.cc: In function ‘void process_command_file(const char*, bool)’:
input.cc:504: warning: ignoring return value of ‘int chdir(const char*)’, declared with attribute warn_unused_result
input.cc:553: warning: ignoring return value of ‘char* getcwd(char*, size_t)’, declared with attribute warn_unused_result
input.cc: In function ‘void cli_main()’:
input.cc:667: error: ‘rl_callback_read_char’ was not declared in this scope
input.cc: In function ‘char** gpsim_completion(const char*, int, int)’:
input.cc:740: error: ‘rl_completion_matches’ was not declared in this scope
input.cc: In function ‘gboolean keypressed(GIOChannel*, GIOCondition, void*)’:
input.cc:773: error: ‘rl_callback_read_char’ was not declared in this scope
input.cc: In function ‘void have_line(char*)’:
input.cc:803: error: ‘add_history’ was not declared in this scope
input.cc: In function ‘void exit_cli()’:
input.cc:831: error: ‘rl_callback_handler_remove’ was not declared in this scope
input.cc: In function ‘void redisplay_prompt()’:
input.cc:856: error: ‘rl_forced_update_display’ was not declared in this scope
input.cc: In function ‘void initialize_readline()’:
input.cc:900: error: ‘rl_getc_function’ was not declared in this scope
input.cc:921: error: ‘rl_callback_handler_install’ was not declared in this scope
input.cc:924: error: ‘rl_attempted_completion_function’ was not declared in this scope
make[2]: *** [input.lo] Error 1
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0'
make: *** [all] Error 2
root@votrecauchemar:~/Escritorio/gpsim-0.24.0# install make
install: falta el operando archivo de destino después de «make»
Pruebe «install --help» para obtener más información.

```

---

### Post by steveneddy on 2010-05-26
The final command is supposed to be

```
make install
```

NOT

**install make**

---

### Post by LePresident on 2010-05-26
> **steveneddy said:**
> The final command is supposed to be

```
make install
```NOT

**install make**


No improve... any other suggestion? :S

---

### Post by steveneddy on 2010-05-26
> **LePresident said:**
> No improve... any other suggestion? :S

You will have to tell us exactly how you entered the command and if you

./configure
make

first before you

make install

or simply post the output of your terminal.

If you closed the terminal then you will have to start over by 

```
cd
```

to the folder in terminal and starting the process again.



remember that we can't see what you are doing, you must provide that info to us to get the proper response to your issue.

---

### Post by LePresident on 2010-05-27
This is what I do:

```
root@votrecauchemar:~/Escritorio/gpsim-0.24.0# [SIZE=3][COLOR=Red]**./configure**[/COLOR][/SIZE]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
enabling gui support
disabling gpsim socket interface
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking popt.h usability... yes
checking popt.h presence... yes
checking for popt.h... yes
checking for pkg-config... /usr/bin/pkg-config
linking with gtk-2.20.0
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for main in -lpopt... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking return type of signal handlers... void
checking for working alloca.h... yes
checking for alloca... yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for working strtod... yes
checking for floor... yes
checking for gethostbyname... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for memset... yes
checking for pow... yes
checking for select... yes
checking for socket... yes
checking for sqrt... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strndup... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtoul... yes
checking size of long... 4
configure: creating ./config.status
config.status: creating Makefile
config.status: creating cli/Makefile
config.status: creating doc/Makefile
config.status: creating examples/Makefile
config.status: creating examples/modules/Makefile
config.status: creating examples/projects/Makefile
config.status: creating eXdbm/Makefile
config.status: creating gpsim/Makefile
config.status: creating gui/Makefile
config.status: creating modules/Makefile
config.status: creating regression/Makefile
config.status: creating src/Makefile
config.status: creating src/dspic/Makefile
config.status: creating xpms/Makefile
config.status: creating gpsim.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


gpsim-0.24.0 is now configured for 

  Build:                i686-pc-linux-gnu
  Host:                 i686-pc-linux-gnu
  Source directory:     .
  Installation prefix:  /usr/local
  C compiler:           gcc  -g -O2 -Wall
  C++ compiler:         g++  -g -O2 -Wall

  gui:                  yes
  Socket interface:     no


root@votrecauchemar:~/Escritorio/gpsim-0.24.0# [SIZE=3][COLOR=Red]**make**[/COLOR][/SIZE]
make  all-recursive
make[1]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0'
Making all in eXdbm
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
Making all in src
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making all in dspic
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: No se hace nada para `all'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[3]: No se hace nada para `all-am'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making all in cli
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c -o input.lo input.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.cc  -fPIC -DPIC -o .libs/input.o
input.cc:86:31: error: readline/readline.h: No existe el fichero ó directorio
input.cc:87:30: error: readline/history.h: No existe el fichero ó directorio
input.cc: In function &#8216;void process_command_file(const char*, bool)&#8217;:
input.cc:504: warning: ignoring return value of &#8216;int chdir(const char*)&#8217;, declared with attribute warn_unused_result
input.cc:553: warning: ignoring return value of &#8216;char* getcwd(char*, size_t)&#8217;, declared with attribute warn_unused_result
input.cc: In function &#8216;void cli_main()&#8217;:
input.cc:667: error: &#8216;rl_callback_read_char&#8217; was not declared in this scope
input.cc: In function &#8216;char** gpsim_completion(const char*, int, int)&#8217;:
input.cc:740: error: &#8216;rl_completion_matches&#8217; was not declared in this scope
input.cc: In function &#8216;gboolean keypressed(GIOChannel*, GIOCondition, void*)&#8217;:
input.cc:773: error: &#8216;rl_callback_read_char&#8217; was not declared in this scope
input.cc: In function &#8216;void have_line(char*)&#8217;:
input.cc:803: error: &#8216;add_history&#8217; was not declared in this scope
input.cc: In function &#8216;void exit_cli()&#8217;:
input.cc:831: error: &#8216;rl_callback_handler_remove&#8217; was not declared in this scope
input.cc: In function &#8216;void redisplay_prompt()&#8217;:
input.cc:856: error: &#8216;rl_forced_update_display&#8217; was not declared in this scope
input.cc: In function &#8216;void initialize_readline()&#8217;:
input.cc:900: error: &#8216;rl_getc_function&#8217; was not declared in this scope
input.cc:921: error: &#8216;rl_callback_handler_install&#8217; was not declared in this scope
input.cc:924: error: &#8216;rl_attempted_completion_function&#8217; was not declared in this scope
make[2]: *** [input.lo] Error 1
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0'
make: *** [all] Error 2


root@votrecauchemar:~/Escritorio/gpsim-0.24.0#[SIZE=3]** [COLOR=Red]make install[/COLOR]**[/SIZE]
Making install in eXdbm
make[1]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libgpsim_eXdbm.la '/usr/local/lib'
/usr/bin/install -c .libs/libgpsim_eXdbm.so.0.0.0 /usr/local/lib/libgpsim_eXdbm.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgpsim_eXdbm.so.0.0.0 libgpsim_eXdbm.so.0 || { rm -f libgpsim_eXdbm.so.0 && ln -s libgpsim_eXdbm.so.0.0.0 libgpsim_eXdbm.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgpsim_eXdbm.so.0.0.0 libgpsim_eXdbm.so || { rm -f libgpsim_eXdbm.so && ln -s libgpsim_eXdbm.so.0.0.0 libgpsim_eXdbm.so; }; })
/usr/bin/install -c .libs/libgpsim_eXdbm.lai /usr/local/lib/libgpsim_eXdbm.la
/usr/bin/install -c .libs/libgpsim_eXdbm.a /usr/local/lib/libgpsim_eXdbm.a
chmod 644 /usr/local/lib/libgpsim_eXdbm.a
ranlib /usr/local/lib/libgpsim_eXdbm.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include/eXdbm" || /bin/mkdir -p "/usr/local/include/eXdbm"
 /usr/bin/install -c -m 644 eXdbm.h eXdbmErrors.h eXdbmTypes.h '/usr/local/include/eXdbm'
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
make[1]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
Making install in src
make[1]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making install in dspic
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c   libgpsim_dspic.la '/usr/local/lib'
/usr/bin/install -c .libs/libgpsim_dspic.so.0.0.0 /usr/local/lib/libgpsim_dspic.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgpsim_dspic.so.0.0.0 libgpsim_dspic.so.0 || { rm -f libgpsim_dspic.so.0 && ln -s libgpsim_dspic.so.0.0.0 libgpsim_dspic.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgpsim_dspic.so.0.0.0 libgpsim_dspic.so || { rm -f libgpsim_dspic.so && ln -s libgpsim_dspic.so.0.0.0 libgpsim_dspic.so; }; })
/usr/bin/install -c .libs/libgpsim_dspic.lai /usr/local/lib/libgpsim_dspic.la
/usr/bin/install -c .libs/libgpsim_dspic.a /usr/local/lib/libgpsim_dspic.a
chmod 644 /usr/local/lib/libgpsim_dspic.a
ranlib /usr/local/lib/libgpsim_dspic.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: No se hace nada para `install-data-am'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libgpsim.la '/usr/local/lib'
/usr/bin/install -c .libs/libgpsim.so.0.0.0 /usr/local/lib/libgpsim.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgpsim.so.0.0.0 libgpsim.so.0 || { rm -f libgpsim.so.0 && ln -s libgpsim.so.0.0.0 libgpsim.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgpsim.so.0.0.0 libgpsim.so || { rm -f libgpsim.so && ln -s libgpsim.so.0.0.0 libgpsim.so; }; })
/usr/bin/install -c .libs/libgpsim.lai /usr/local/lib/libgpsim.la
/usr/bin/install -c .libs/libgpsim.a /usr/local/lib/libgpsim.a
chmod 644 /usr/local/lib/libgpsim.a
ranlib /usr/local/lib/libgpsim.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include/gpsim" || /bin/mkdir -p "/usr/local/include/gpsim"
 /usr/bin/install -c -m 644 12bit-instructions.h 12bit-processors.h 14bit-instructions.h 14bit-processors.h 14bit-registers.h 14bit-tmrs.h 16bit-instructions.h 16bit-processors.h 16bit-registers.h 16bit-tmrs.h a2dconverter.h a2d_v2.h attributes.h bit.h bitlog.h breakpoints.h bytelog.h clock_phase.h cmd_gpsim.h cmd_manager.h cod.h comparator.h eeprom.h exports.h hexutils.h i2c-ee.h fopen-path.h gpsim_classes.h gpsim_def.h gpsim_interface.h gpsim_object.h gpsim_time.h intcon.h interface.h ioports.h lxt_write.h modules.h operator.h p12f6xx.h p12x.h '/usr/local/include/gpsim'
 /usr/bin/install -c -m 644 p16x5x.h p16f62x.h p16x6x.h p16x7x.h p16x8x.h p16f8x.h p16f87x.h p17c75x.h p18x.h packages.h pic-instructions.h pic-packages.h pic-processor.h pic-registers.h pic-ioports.h picdis.h pie.h pir.h pm_rd.h processor.h program_files.h protocol.h pthread-wrap.h registers.h rcon.h sim_context.h stimuli.h symbol.h tmr0.h trace.h trigger.h trace_orb.h ttoken.h uart.h xref.h icd.h ssp.h psp.h errors.h expr.h '/usr/local/include/gpsim'
 /usr/bin/install -c -m 644 ui.h value.h ValueCollections.h '/usr/local/include/gpsim'
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[1]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making install in cli
make[1]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c -o input.lo input.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.cc  -fPIC -DPIC -o .libs/input.o
input.cc:86:31: error: readline/readline.h: No existe el fichero ó directorio
input.cc:87:30: error: readline/history.h: No existe el fichero ó directorio
input.cc: In function &#8216;void process_command_file(const char*, bool)&#8217;:
input.cc:504: warning: ignoring return value of &#8216;int chdir(const char*)&#8217;, declared with attribute warn_unused_result
input.cc:553: warning: ignoring return value of &#8216;char* getcwd(char*, size_t)&#8217;, declared with attribute warn_unused_result
input.cc: In function &#8216;void cli_main()&#8217;:
input.cc:667: error: &#8216;rl_callback_read_char&#8217; was not declared in this scope
input.cc: In function &#8216;char** gpsim_completion(const char*, int, int)&#8217;:
input.cc:740: error: &#8216;rl_completion_matches&#8217; was not declared in this scope
input.cc: In function &#8216;gboolean keypressed(GIOChannel*, GIOCondition, void*)&#8217;:
input.cc:773: error: &#8216;rl_callback_read_char&#8217; was not declared in this scope
input.cc: In function &#8216;void have_line(char*)&#8217;:
input.cc:803: error: &#8216;add_history&#8217; was not declared in this scope
input.cc: In function &#8216;void exit_cli()&#8217;:
input.cc:831: error: &#8216;rl_callback_handler_remove&#8217; was not declared in this scope
input.cc: In function &#8216;void redisplay_prompt()&#8217;:
input.cc:856: error: &#8216;rl_forced_update_display&#8217; was not declared in this scope
input.cc: In function &#8216;void initialize_readline()&#8217;:
input.cc:900: error: &#8216;rl_getc_function&#8217; was not declared in this scope
input.cc:921: error: &#8216;rl_callback_handler_install&#8217; was not declared in this scope
input.cc:924: error: &#8216;rl_attempted_completion_function&#8217; was not declared in this scope
make[1]: *** [input.lo] Error 1
make[1]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
make: *** [install-recursive] Error 1

```

---

### Post by anglican on 2010-05-28
> **LePresident said:**
> This is what I do:

```

snip
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
snip

root@votrecauchemar:~/Escritorio/gpsim-0.24.0# [SIZE=3][COLOR=Red]**make**[/COLOR][/SIZE]
make  all-recursive
make[1]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0'
Making all in eXdbm
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/eXdbm'
Making all in src
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making all in dspic
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: No se hace nada para `all'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src/dspic'
make[3]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[3]: No se hace nada para `all-am'.
make[3]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/src'
Making all in cli
make[2]: se ingresa al directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c -o input.lo input.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -Wall -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.cc  -fPIC -DPIC -o .libs/input.o
input.cc:86:31: error: readline/readline.h: No existe el fichero ó directorio
input.cc:87:30: error: readline/history.h: No existe el fichero ó directorio
input.cc: In function ‘void process_command_file(const char*, bool)’:
input.cc:504: warning: ignoring return value of ‘int chdir(const char*)’, declared with attribute warn_unused_result
input.cc:553: warning: ignoring return value of ‘char* getcwd(char*, size_t)’, declared with attribute warn_unused_result
input.cc: In function ‘void cli_main()’:
input.cc:667: error: ‘rl_callback_read_char’ was not declared in this scope
input.cc: In function ‘char** gpsim_completion(const char*, int, int)’:
input.cc:740: error: ‘rl_completion_matches’ was not declared in this scope
input.cc: In function ‘gboolean keypressed(GIOChannel*, GIOCondition, void*)’:
input.cc:773: error: ‘rl_callback_read_char’ was not declared in this scope
input.cc: In function ‘void have_line(char*)’:
input.cc:803: error: ‘add_history’ was not declared in this scope
input.cc: In function ‘void exit_cli()’:
input.cc:831: error: ‘rl_callback_handler_remove’ was not declared in this scope
input.cc: In function ‘void redisplay_prompt()’:
input.cc:856: error: ‘rl_forced_update_display’ was not declared in this scope
input.cc: In function ‘void initialize_readline()’:
input.cc:900: error: ‘rl_getc_function’ was not declared in this scope
input.cc:921: error: ‘rl_callback_handler_install’ was not declared in this scope
input.cc:924: error: ‘rl_attempted_completion_function’ was not declared in this scope
make[2]: *** [input.lo] Error 1
make[2]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0/cli'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/votrecauchemar/Escritorio/gpsim-0.24.0'
make: *** [all] Error 2

snip


```
You don't appear to have all the necessary dependencies installed - see the INSTALL file:
> 1.1 Dependencies

The most significant non-common gpsim dependency is on the gtkextra
package: [http://gtkextra.sourceforge.net/](http://gtkextra.sourceforge.net/)

Other dependencies include gtk-2.0, readline, popt. These packages
should be installed on most distributions. However, it should be noted
that the "developer" version are required if you're building gpsim
from the source.

 H

---

### Post by LePresident on 2010-05-28
> **anglican said:**
> You don't appear to have all the necessary dependencies installed - see the INSTALL file:
 H
pfff... is there a way to install gpsim without building it from the source code?

---

### Post by oldos2er on 2010-05-28
> **LePresident said:**
> pfff... is there a way to install gpsim without building it from the source code?

It's in the repositories: ```
sudo apt-get install gpsim
```

---

### Post by Blancmange on 2010-06-10
Unfortunately the current version of gpsim that exists in the repositories is 0.22. In this version, under Ubuntu 8.04 anyway, the disassembly window, the memory window and single-step debugging are about the only features that work. I've never managed to get the scope to work despite the CLI instructions I've issued. The program has to be started, used and exited repeatedly for it to settle down to a stable (but still mostly useless) state.

There's no hope of it running from piklab because gpsim generates spurious low-level parsing errors that are not handled by the higher level parts of the program (so there is no possibility of diagnosis or remedy because gpsim fails to indicate what it was trying to do when it failed). It's way before an alpha release.

The latest source is v0.24. Unfortunately, ./configure doesn't work because it fails to find popt.h on my system. Popt is obsolete and no longer exists in the Ubuntu repositories because it has been replaced by libpopt0. Presumably, ./configure's failure is why "make all" fails to get anywhere far.

A relatively minor problem is that the breadboard modules cannot be loaded by gpsim under Ubuntu. That's because Debian and Ubuntu systems come with module names that gpsim doesn't expect to see and which gpsim refuses to use because it insists on mangling the names the user inputs. That can be fixed by adding symbolic links in the /usr/lib directory.

I tend to wonder about claims of programs being able to run under some OS or variant, sometimes.

If you have a Windows boot, you might might have better luck with the Windows version gpsim until the developers notice that gpsim doesn't run under Ubuntu.

---

