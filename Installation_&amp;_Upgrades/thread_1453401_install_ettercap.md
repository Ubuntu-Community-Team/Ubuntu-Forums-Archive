---
title: "install ettercap"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by LHYX on 2010-04-13
hey,
i'm new to ubuntu and i'm trying to get ettercap to work.
I installed it with the command:
sudo apt-get install etterca-gtk
and the program was installed succesfully.
But when i open the program from the terminal with:
sudo ettercap -G or just open it from applications => internet : ubuntu crashes !
I can't move my mouse and can't do anything.
But if I don't run the applications as root from the terminal :
ettercap -G

The application opens but then I'm noty able to select an interface.

What am I missing here?
please help :)

---

### Post by bboyreason on 2010-04-13
try putting the wireless card into monitor mode before trying the method that worked to open the program;
like use:
sudo airmon-ng wlan0 start
where wlan0 is your card, if you have aircrack suite installed;
i havent used ettercap, but this is what i do to get wireshark to work;
i am pretty new to this too, so i might be wrong;
just trying to help since no one had answered;

---

### Post by LHYX on 2010-04-14
srr but that doesn't do the job.
And normally you should run ettercap as root with sudo.

I red something about compiling ettercap from the sourcecode to fix this problem.
But I don't know how to compile ettercap.

any ideas ? :)

---

### Post by LHYX on 2010-04-14
Now I'm trying to compile ettercap myself to let it work.
I think i have all the necessary libs. And i installed build-assential and build-dep and zlib
with the commands :
sudo apt-get install zlib1g zlib1g-dev
sudo apt-get install build-essential
sudo apt-get install build-dep ettercap
This was all succesfully.

than I downloaded the latest tart file from the ettercap site and extracted the files to my desktop. than I navigate with the terminal to the desktop and I type : sudo ./configure
This is also succesful and gives me this output:

Configuring ettercap NG-0.7.3...

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking if your compiler supports __VA_ARGS__ in macro declarations... yes
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for library containing dlopen... -ldl
checking for an ANSI C-conforming const... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib64 /usr/lib64
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for library containing lt_dlopen... -lltdl
checking for dlfcn.h... (cached) yes
checking ltdl.h usability... yes
checking ltdl.h presence... yes
checking for ltdl.h... yes
checking whether byte ordering is bigendian... no
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for dirent.h that defines DIR... (cached) yes
checking for library containing opendir... (cached) none required
checking for unistd.h... (cached) yes
checking for stdlib.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/types.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for errno.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for ctype.h... (cached) yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking for NS_GET32... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking for size_t... yes
checking for an ANSI C-conforming const... (cached) yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for library containing pthread_create... -lpthread
checking whether gcc accepts -pthread... yes
checking for getifaddrs... yes
checking for gettimeofday... yes
checking for vsnprintf... yes
checking for select... yes
checking for poll... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes
checking for strsignal... yes
checking for strtok_r... yes
checking for uname... yes
checking for daemon... yes

Checking for required libraries...

checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing poll... none required
checking for library containing gzopen... -lz
checking for library containing dn_expand... no

Checking for missing functions...

checking for strlcpy... no
checking for strlcat... no
checking for strsep... yes
checking for memmem... yes
checking for memcmp... yes
checking for basename... yes
checking for getopt_long... yes
checking for strcasestr... yes
checking for scandir... yes
checking for inet_aton... yes
checking for inet_aton in -lresolv... yes

Checking user defined options...

checking if --enable-debug option was specified... no
checking if --enable-plugins option was specified... yes by default
checking for libpcap... yes
checking for pcap_datalink_val_to_description in -lpcap... yes
checking for libnet... yes
checking for libnet_adv_free_packet in -lnet... yes
checking for openssl... yes
checking for libpcre... yes
checking for iconv... yes
checking for library containing iconv... none required
checking for iconv in -lc... yes
checking for iconv in -liconv... no
checking for libiconv in -liconv... no
checking for libncurses... yes
checking if --enable-gtk option was specified... checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK_CFLAGS... -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking for GTK_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lfreetype -lfontconfig -lpango-1.0 -lgmodule-2.0 -latk-1.0 -lgobject-2.0 -lglib-2.0  

Writing output files...

configure: creating ./config.status
config.status: creating Makefile
config.status: creating Makefile.mingw
config.status: creating man/Makefile
config.status: creating man/ettercap.8
config.status: creating man/ettercap_curses.8
config.status: creating man/ettercap_plugins.8
config.status: creating man/etterlog.8
config.status: creating man/etterfilter.8
config.status: creating man/etter.conf.5
config.status: creating share/Makefile
config.status: creating src/Makefile
config.status: creating src/os/Makefile
config.status: creating src/interfaces/Makefile
config.status: creating src/interfaces/daemon/Makefile
config.status: creating src/interfaces/text/Makefile
config.status: creating src/interfaces/curses/Makefile
config.status: creating src/interfaces/curses/widgets/Makefile
config.status: creating src/interfaces/gtk/Makefile
config.status: creating include/Makefile
config.status: creating utils/Makefile
config.status: creating utils/etterlog/Makefile
config.status: creating utils/etterfilter/Makefile
config.status: creating plug-ins/Makefile
config.status: creating plug-ins/arp_cop/Makefile
config.status: creating plug-ins/autoadd/Makefile
config.status: creating plug-ins/chk_poison/Makefile
config.status: creating plug-ins/dos_attack/Makefile
config.status: creating plug-ins/dns_spoof/Makefile
config.status: creating plug-ins/dummy/Makefile
config.status: creating plug-ins/find_conn/Makefile
config.status: creating plug-ins/find_ettercap/Makefile
config.status: creating plug-ins/find_ip/Makefile
config.status: creating plug-ins/finger/Makefile
config.status: creating plug-ins/finger_submit/Makefile
config.status: creating plug-ins/gre_relay/Makefile
config.status: creating plug-ins/gw_discover/Makefile
config.status: creating plug-ins/isolate/Makefile
config.status: creating plug-ins/link_type/Makefile
config.status: creating plug-ins/pptp_chapms1/Makefile
config.status: creating plug-ins/pptp_clear/Makefile
config.status: creating plug-ins/pptp_pap/Makefile
config.status: creating plug-ins/pptp_reneg/Makefile
config.status: creating plug-ins/rand_flood/Makefile
config.status: creating plug-ins/remote_browser/Makefile
config.status: creating plug-ins/reply_arp/Makefile
config.status: creating plug-ins/repoison_arp/Makefile
config.status: creating plug-ins/scan_poisoner/Makefile
config.status: creating plug-ins/search_promisc/Makefile
config.status: creating plug-ins/smb_clear/Makefile
config.status: creating plug-ins/smb_down/Makefile
config.status: creating plug-ins/stp_mangler/Makefile
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands

ettercap has been configured as follow...

==================================================

 Install directory:  /usr/local


Libraries : 

 LIBPCAP ................  default
 LIBNET .................  default
 LIBSSL .................  default
 NCURSES ................  default
 GTK+ ...................  yes

Functionalities : 

 Debug mode .............  no
 Plugin support .........  yes
 Passive DNS ............  no
 Perl regex in filters ..  yes
 Iconv UTF-8 support ....  yes

==================================================


But then when I try to type make it starts doing stuff but eventually it get an error:

Making all in man
make[1]: Entering directory `/home/lhyx/Bureaublad/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lhyx/Bureaublad/man'
Making all in share
make[1]: Entering directory `/home/lhyx/Bureaublad/share'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lhyx/Bureaublad/share'
Making all in include
make[1]: Entering directory `/home/lhyx/Bureaublad/include'
make  all-am
make[2]: Entering directory `/home/lhyx/Bureaublad/include'
make[2]: Leaving directory `/home/lhyx/Bureaublad/include'
make[1]: Leaving directory `/home/lhyx/Bureaublad/include'
Making all in include
make[1]: Entering directory `/home/lhyx/Bureaublad/include'
make  all-am
make[2]: Entering directory `/home/lhyx/Bureaublad/include'
make[2]: Leaving directory `/home/lhyx/Bureaublad/include'
make[1]: Leaving directory `/home/lhyx/Bureaublad/include'
Making all in src
make[1]: Entering directory `/home/lhyx/Bureaublad/src'
Making all in os
make[2]: Entering directory `/home/lhyx/Bureaublad/src/os'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lhyx/Bureaublad/src/os'
Making all in interfaces
make[2]: Entering directory `/home/lhyx/Bureaublad/src/interfaces'
Making all in daemon
make[3]: Entering directory `/home/lhyx/Bureaublad/src/interfaces/daemon'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces/daemon'
Making all in text
make[3]: Entering directory `/home/lhyx/Bureaublad/src/interfaces/text'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces/text'
Making all in curses
make[3]: Entering directory `/home/lhyx/Bureaublad/src/interfaces/curses'
Making all in widgets
make[4]: Entering directory `/home/lhyx/Bureaublad/src/interfaces/curses/widgets'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces/curses/widgets'
make[4]: Entering directory `/home/lhyx/Bureaublad/src/interfaces/curses'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces/curses'
make[3]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces/curses'
Making all in gtk
make[3]: Entering directory `/home/lhyx/Bureaublad/src/interfaces/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces/gtk'
make[3]: Entering directory `/home/lhyx/Bureaublad/src/interfaces'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces'
make[2]: Leaving directory `/home/lhyx/Bureaublad/src/interfaces'
make[2]: Entering directory `/home/lhyx/Bureaublad/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include    -O2 -funroll-loops -fomit-frame-pointer -Wall -I/usr/include/pcap     -g -O2 -MT ettercap-ec_log.o -MD -MP -MF ".deps/ettercap-ec_log.Tpo" -c -o ettercap-ec_log.o `test -f 'ec_log.c' || echo './'`ec_log.c; \
    then mv -f ".deps/ettercap-ec_log.Tpo" ".deps/ettercap-ec_log.Po"; else rm -f ".deps/ettercap-ec_log.Tpo"; exit 1; fi
ec_log.c: In function ‘log_packet’:
ec_log.c:248: warning: pointer targets in passing argument 2 of ‘regexec’ differ in signedness
/usr/include/regex.h:571: note: expected ‘const char * __restrict__’ but argument is of type ‘u_char *’
ec_log.c: In function ‘log_write_info’:
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:397: note: expected ‘const char *’ but argument is of type ‘u_char *’
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: note: expected ‘const char *’ but argument is of type ‘u_char *’
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:397: note: expected ‘const char *’ but argument is of type ‘u_char *’
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: note: expected ‘const char *’ but argument is of type ‘u_char *’
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: note: expected ‘const char *’ but argument is of type ‘u_char *’
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: note: expected ‘const char *’ but argument is of type ‘u_char *’
In file included from /usr/include/fcntl.h:217,
                 from ec_log.c:32:
In function ‘open’,
    inlined from ‘log_open’ at ec_log.c:193:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [ettercap-ec_log.o] Error 1
make[2]: Leaving directory `/home/lhyx/Bureaublad/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lhyx/Bureaublad/src'
make: *** [all-recursive] Error 1

please help !!

---

### Post by LHYX on 2010-04-18
Solved !!!!
Now I use ubuntu 8.0.4 in place of the newest version.
I just installed ettercap from the add/remove programs and it worked !!
:D

---

### Post by randumnumber on 2010-10-24
I would like to add. I have 10.04 and just installed ettercap no problem by doing System>Admin>Synaptic>Password>Search for ettercap and select the Common and ettercap-gtk tabs for a GUI(graphical user interface). or Common and ettercap for a CLI(command line interface)

---

