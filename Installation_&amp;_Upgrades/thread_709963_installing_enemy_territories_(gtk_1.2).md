---
title: "installing enemy territories (gtk 1.2)"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by sujinge9 on 2008-02-27
I'm trying to install enemy territories but its asking for gtk 1.2. I just spent a few weeks getting gtk 2.x installed and now I have to get 1.2... This is what I'm getting
```
jinge@jinge-desktop:~/Desktop$ sudo sh et-linux-2.55.x86.run
[sudo] password for jinge:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/jinge/.setup20020: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting
jinge@jinge-desktop:~/Desktop$ ls
56961-GRUB-Splashies         glib-1.2.10         Nexuiz
56961-GRUB-Splashies.tar.gz  glib-1.2.10.tar.gz  nexuiz-23.zip
73135-Obsidian.tar.bz2       gridwars            Obsidian
et-linux-2.55.x86.run        nexmappack_r2.zip   pbsetup.run
jinge@jinge-desktop:~/Desktop$ cd glib-1.2.10
jinge@jinge-desktop:~/Desktop/glib-1.2.10$ ./configure
./configure: 464: cannot create ./config.log: Permission denied
jinge@jinge-desktop:~/Desktop/glib-1.2.10$ sudo configure
sudo: configure: command not found
jinge@jinge-desktop:~/Desktop/glib-1.2.10$ sudo ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
loading cache ./config.cache within ltconfig
checking for object suffix... o
checking for executable suffix... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
loading cache ./config.cache
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
checking whether to enable memory checking... no
checking whether to enable memory profiling... no
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for a BSD compatible install... /usr/bin/install -c
checking for extra flags to get ANSI library prototypes... none needed
checking for extra flags for POSIX compliance... none needed
checking how to run the C preprocessor... (cached) gcc -E
checking for ANSI C header files... (cached) yes
checking for vprintf... (cached) yes
checking for atexit... (cached) yes
checking for on_exit... (cached) yes
checking size of char... (cached) 1
checking size of short... (cached) 2
checking size of long... (cached) 4
checking size of int... (cached) 4
checking size of void *... (cached) 4
checking size of long long... (cached) 8
checking for working const... (cached) yes
checking for __inline... (cached) yes
checking for __inline__... (cached) yes
checking for inline... (cached) yes
checking whether byte ordering is bigendian... (cached) no
checking for float.h... (cached) yes
checking for limits.h... (cached) yes
checking for pwd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for sys/poll.h... (cached) yes
checking for sys/select.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for sys/times.h... (cached) yes
checking for unistd.h... (cached) yes
checking for values.h... (cached) yes
checking for lstat... (cached) yes
checking for strerror... (cached) yes
checking for strsignal... (cached) yes
checking for memmove... (cached) yes
checking for vsnprintf... (cached) yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... (cached) yes
checking for poll... (cached) yes
checking for sys_errlist... yes
checking for sys_siglist... yes
checking for sys_siglist declaration... yes
checking for fd_set... yes, found in sys/types.h
checking for wchar.h... yes
checking for wctype.h... yes
checking for iswalnum... (cached) yes
checking if iswalnum() and friends are properly defined... yes
checking whether realloc (NULL,) will work... (cached) yes
checking for an implementation of va_copy()... (cached) yes
checking for an implementation of __va_copy()... (cached) yes
checking whether va_lists can be copied by value... (cached) yes
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlsym in -ldl... (cached) yes
checking for RTLD_GLOBAL brokenness... (cached) no
checking for preceeding underscore in symbols... (cached) no
checking for dlerror... (cached) yes
checking for pthread.h... (cached) yes
checking for thread implementation... posix
checking for pthread_attr_init in -lpthread... (cached) yes
checking necessary linker options... -lpthread
checking necessary compiler options...  -D_REENTRANT
checking for localtime_r... (cached) yes
checking for rand_r... (cached) yes
checking for getpwuid_r... (cached) yes
checking whether getpwuid_r is posix like... yes
checking whether pthread_getspecific is posix like... yes
checking whether pthread_mutex_trylock is posix like... yes
checking whether pthread_cond_timedwait is posix like... yes
checking size of pthread_mutex_t... (cached) 24
checking byte contents of pthread_mutex_t... (cached) 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
checking system definitions for POLLIN POLLOUT POLLPRI POLLERR POLLHUP POLLNVAL... done
creating ./config.status
creating glib.spec
creating Makefile
creating glib-config
creating gmodule/gmoduleconf.h
creating gmodule/Makefile
creating gthread/Makefile
creating docs/Makefile
creating docs/glib-config.1
creating tests/Makefile
creating glib.pc
creating gmodule.pc
creating gthread.pc
creating config.h
creating glibconfig.h
glibconfig.h is unchanged
jinge@jinge-desktop:~/Desktop/glib-1.2.10$ sudo make
make  all-recursive
make[1]: Entering directory `/home/jinge/Desktop/glib-1.2.10'
Making all in .
make[2]: Entering directory `/home/jinge/Desktop/glib-1.2.10'
CONFIG_FILES= CONFIG_HEADERS= CONFIG_OTHER=glibconfig.h ./config.status
creating glibconfig.h
glibconfig.h is unchanged
echo timestamp > stamp-gc-h
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gdate.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gdate.c  -fPIC -DPIC -o .libs/gdate.lo
gdate.c: In function 'g_date_fill_parse_tokens':
gdate.c:463: warning: pointer targets in assignment differ in signedness
gdate.c: In function 'g_date_set_parse':
gdate.c:666: warning: type-punning to incomplete type might break strict-aliasing rules
gdate.c:678: warning: type-punning to incomplete type might break strict-aliasing rules
gdate.c:796: warning: type-punning to incomplete type might break strict-aliasing rules
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gdate.c -o gdate.o >/dev/null 2>&1
mv -f .libs/gdate.lo gdate.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gerror.c
rm -f .libs/gerror.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gerror.c  -fPIC -DPIC -o .libs/gerror.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gerror.c -o gerror.o >/dev/null 2>&1
mv -f .libs/gerror.lo gerror.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c giochannel.c
rm -f .libs/giochannel.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c giochannel.c  -fPIC -DPIC -o .libs/giochannel.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c giochannel.c -o giochannel.o >/dev/null 2>&1
mv -f .libs/giochannel.lo giochannel.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gmain.c
rm -f .libs/gmain.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gmain.c  -fPIC -DPIC -o .libs/gmain.lo
gmain.c: In function 'g_source_destroy_func':
gmain.c:435: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:445: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_source_add':
gmain.c:459: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:490: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_source_remove':
gmain.c:502: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:508: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_source_remove_by_user_data':
gmain.c:518: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:524: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_source_remove_by_source_data':
gmain.c:543: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:550: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_source_remove_by_funcs_user_data':
gmain.c:573: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:583: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_main_dispatch':
gmain.c:655: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:659: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_main_iterate':
gmain.c:717: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:723: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:734: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:769: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:774: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:783: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:841: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:846: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:863: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:881: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_main_poll':
gmain.c:1033: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:1035: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_main_add_poll':
gmain.c:1114: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:1116: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c: In function 'g_main_remove_poll':
gmain.c:1172: warning: type-punning to incomplete type might break strict-aliasing rules
gmain.c:1203: warning: type-punning to incomplete type might break strict-aliasing rules
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gmain.c -o gmain.o >/dev/null 2>&1
mv -f .libs/gmain.lo gmain.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gmem.c
rm -f .libs/gmem.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gmem.c  -fPIC -DPIC -o .libs/gmem.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gmem.c -o gmem.o >/dev/null 2>&1
mv -f .libs/gmem.lo gmem.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gmessages.c
rm -f .libs/gmessages.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gmessages.c  -fPIC -DPIC -o .libs/gmessages.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gmessages.c -o gmessages.o >/dev/null 2>&1
mv -f .libs/gmessages.lo gmessages.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gscanner.c
rm -f .libs/gscanner.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gscanner.c  -fPIC -DPIC -o .libs/gscanner.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gscanner.c -o gscanner.o >/dev/null 2>&1
mv -f .libs/gscanner.lo gscanner.lo
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gstrfuncs.c
rm -f .libs/gstrfuncs.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gstrfuncs.c  -fPIC -DPIC -o .libs/gstrfuncs.lo
gstrfuncs.c: In function 'g_printf_string_upper_bound':
gstrfuncs.c:870: error: expected ')' before string constant
gstrfuncs.c:1037: error: expected ')' before string constant
gstrfuncs.c:1080: error: expected ')' before string constant
gstrfuncs.c:1111: error: expected ')' before string constant
gstrfuncs.c: In function 'g_strdown':
gstrfuncs.c:1139: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strup':
gstrfuncs.c:1155: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strchug':
gstrfuncs.c:1314: warning: pointer targets in assignment differ in signedness
gstrfuncs.c:1317: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
make[2]: *** [gstrfuncs.lo] Error 1
make[2]: Leaving directory `/home/jinge/Desktop/glib-1.2.10'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jinge/Desktop/glib-1.2.10'
make: *** [all-recursive-am] Error 2
jinge@jinge-desktop:~/Desktop/glib-1.2.10$ sudo make install
Making install in .
make[1]: Entering directory `/home/jinge/Desktop/glib-1.2.10'
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gstrfuncs.c
rm -f .libs/gstrfuncs.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gstrfuncs.c  -fPIC -DPIC -o .libs/gstrfuncs.lo
gstrfuncs.c: In function 'g_printf_string_upper_bound':
gstrfuncs.c:870: error: expected ')' before string constant
gstrfuncs.c:1037: error: expected ')' before string constant
gstrfuncs.c:1080: error: expected ')' before string constant
gstrfuncs.c:1111: error: expected ')' before string constant
gstrfuncs.c: In function 'g_strdown':
gstrfuncs.c:1139: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strup':
gstrfuncs.c:1155: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strchug':
gstrfuncs.c:1314: warning: pointer targets in assignment differ in signedness
gstrfuncs.c:1317: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
make[1]: *** [gstrfuncs.lo] Error 1
make[1]: Leaving directory `/home/jinge/Desktop/glib-1.2.10'
make: *** [install-recursive] Error 1
jinge@jinge-desktop:~/Desktop/glib-1.2.10$ 

```

---

### Post by aidanr on 2008-02-27
try
```
sudo apt-get install libgtk1.2
```

---

