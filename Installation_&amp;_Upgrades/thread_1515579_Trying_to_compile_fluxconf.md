---
title: "Trying to compile fluxconf"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by jef3189 on 2010-06-22
Hi, I'm trying to compile fluxconf from source ([here]("http://go2.wordpress.com/?id=725X1342&site=linuxcritic.wordpress.com&url=http%3A%2F%2Fdevaux.fabien.free.fr%2Fflux%2Ffluxconf-0.9.9.tar.gz&sref=http%3A%2F%2Flinuxcritic.wordpress.com%2F2009%2F09%2F18%2Ffluxconf-configuring-fluxbox-the-graphical-way%2F")). It's a graphical ui for setting up the menus in fluxbox. 

I've got all the libraries, but when I compile it says:

```

cc1: warnings being treated as errors
fluxconf.c: In function ‘sauver’:
fluxconf.c:244: error: format not a string literal and no format arguments
fluxconf.c:187: error: ignoring return value of ‘write’, declared with attribute warn_unused_result
make[2]: *** [fluxconf-fluxconf.o] Error 1
make[2]: Leaving directory `/home/josh/fluxconf-0.9.9/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/fluxconf-0.9.9/src'
make: *** [all-recursive] Error 1

```that doesn't look like a dependency issue and other people seem to be able to compile/make this just fine with no problems. How can I get this to compile?

Thanks!

---

### Post by jef3189 on 2010-06-22
here's the full output of the ./configure and make
```

# ./configure
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
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ranlib... ranlib
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: ./config.rpath: No such file or directory
done
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getc_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for memset... yes
checking for strcasecmp... (cached) yes
checking for gtk-config... no
checking for gtk12-config... no
checking for pkg-config... /usr/bin/pkg-config
Using pkg-config...
Found Gtk2 ! Compiling using Gtk2...
configure: creating ./config.status
config.status: creating Makefile
config.status: creating docs/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
config.status: executing default-1 commands
``````
# make
Making all in src
make[1]: Entering directory `/home/josh/fluxconf-0.9.9/src'
make[2]: Entering directory `/home/josh/fluxconf-0.9.9/src'
if gcc -DPACKAGE_NAME=\"fluxconf\" -DPACKAGE_TARNAME=\"fluxconf\" -DPACKAGE_VERSION=\"0.9.7b\" -DPACKAGE_STRING=\"fluxconf\ 0.9.7b\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fluxconf\" -DVERSION=\"0.9.7b\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_STRINGS_H=1 -DHAVE_ALLOCA_H=1 -DHAVE_ALLOCA=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DINTDIV0_RAISES_SIGFPE=1 -DHAVE_INTTYPES_H_WITH_UINTMAX=1 -DHAVE_STDINT_H_WITH_UINTMAX=1 -DHAVE_UNSIGNED_LONG_LONG=1 -DHAVE_UINTMAX_T=1 -DHAVE_INTTYPES_H=1 -DHAVE_ARGZ_H=1 -DHAVE_LIMITS_H=1 -DHAVE_LOCALE_H=1 -DHAVE_NL_TYPES_H=1 -DHAVE_MALLOC_H=1 -DHAVE_STDDEF_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_FEOF_UNLOCKED=1 -DHAVE_FGETS_UNLOCKED=1 -DHAVE_GETC_UNLOCKED=1 -DHAVE_GETCWD=1 -DHAVE_GETEGID=1 -DHAVE_GETEUID=1 -DHAVE_GETGID=1 -DHAVE_GETUID=1 -DHAVE_MEMPCPY=1 -DHAVE_MUNMAP=1 -DHAVE_PUTENV=1 -DHAVE_SETENV=1 -DHAVE_SETLOCALE=1 -DHAVE_STPCPY=1 -DHAVE_STRCASECMP=1 -DHAVE_STRDUP=1 -DHAVE_STRTOUL=1 -DHAVE_TSEARCH=1 -DHAVE___ARGZ_COUNT=1 -DHAVE___ARGZ_STRINGIFY=1 -DHAVE___ARGZ_NEXT=1 -DHAVE___FSETLOCKING=1 -DHAVE_ICONV=1 -DICONV_CONST= -DHAVE_LANGINFO_CODESET=1 -DHAVE_LC_MESSAGES=1 -DENABLE_NLS=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_MEMSET=1 -DHAVE_STRCASECMP=1  -I. -I.    -Iinclude/ -Ixpm/ -ggdb -D_GNU_SOURCE -Werror -g -O2 -DLOCALEDIR=\"/usr/local/share/locale\" -ansi -Wall -W -DGTK2 -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -MT fluxconf-fluxconf.o -MD -MP -MF ".deps/fluxconf-fluxconf.Tpo" \
          -c -o fluxconf-fluxconf.o `test -f 'fluxconf.c' || echo './'`fluxconf.c; \
        then mv -f ".deps/fluxconf-fluxconf.Tpo" ".deps/fluxconf-fluxconf.Po"; \
        else rm -f ".deps/fluxconf-fluxconf.Tpo"; exit 1; \
        fi
cc1: warnings being treated as errors
fluxconf.c: In function &#8216;sauver&#8217;:
fluxconf.c:244: error: format not a string literal and no format arguments
fluxconf.c:187: error: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
make[2]: *** [fluxconf-fluxconf.o] Error 1
make[2]: Leaving directory `/home/josh/fluxconf-0.9.9/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/fluxconf-0.9.9/src'
make: *** [all-recursive] Error 1

```

also, why is it treating the warnings as errors? I don't see Werror flag anywhere in the makefile.

---

