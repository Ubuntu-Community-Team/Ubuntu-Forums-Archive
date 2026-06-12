---
title: "Could not exec dpkg! E: Sub-process /usr/bin/dpkg returned an error code (100)"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2011-10-07
Hey all, i'm trying to update my system and install some packages but for some reason i'm getting this error code. anyone know what's going on here? 

```
user@home-desktop:~$ sudo apt-get install  openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

Thanks, 
SlashWannabe94

---

### Post by drs305 on 2011-10-07
I did a search of the error message (the last line of your post).

Some solutions pointed to permission problems with dpkg.

What is the result of:
```
ls -la /usr/bin/dpkg
```
It should look  at lot like:
> **-rwxr-xr-x 1 root root **249328 2011-10-06 04:04 **/usr/bin/dpkg**

---

### Post by slashwannabe94 on 2011-10-08
I think i know what it is now. /usr/bin/dpkg doesn't exist at all. How do i recover from this? 

```
root@home-desktop:~# ls -la /usr/bin/dpkg
ls: cannot access /usr/bin/dpkg: No such file or directory

```

---

### Post by linuxsyst on 2011-10-08
usually it's a permission on dpkg since it can only run as super user. since it's not there than it was deleted.

You would simply download the dpkg package and extract it. you might have to run configure on it but that's about it.

---

### Post by slashwannabe94 on 2011-10-08
I have downloaded the package from source and extracted it. I have ran the ```
./configure  make  and   make install
``` commands and i got this. 

./configure
```
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking dpkg cpu type... i386
checking dpkg operating system type... linux
checking dpkg architecture name... i386
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for flex... no
checking for lex... no
checking for ranlib... ranlib
checking for doxygen... no
checking for dot... NO
checking for po4a... no
checking for perl... /usr/bin/perl
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for gzdopen in -lz... no
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for BZ2_bzdopen in -lbz2... no
checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for is_selinux_enabled in -lselinux... no
checking selinux/selinux.h usability... no
checking selinux/selinux.h presence... no
checking for selinux/selinux.h... no
checking ncursesw/ncurses.h usability... no
checking ncursesw/ncurses.h presence... no
checking for ncursesw/ncurses.h... no
checking ncurses/ncurses.h usability... no
checking ncurses/ncurses.h presence... no
checking for ncurses/ncurses.h... no
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
checking ncursesw/term.h usability... no
checking ncursesw/term.h presence... no
checking for ncursesw/term.h... no
checking ncurses/term.h usability... no
checking ncurses/term.h presence... no
checking for ncurses/term.h... no
checking term.h usability... no
checking term.h presence... no
checking for term.h... no
checking for initscr in -lncursesw... no
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
checking for ihash_create in -lihash... no
checking for proc_stat_list_create in -lps... no
checking for fmt_past_time in -lshouldbeinlibc... no
checking for kvm_openfiles in -lkvm... no
checking for ANSI C header files... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking error.h usability... yes
checking error.h presence... yes
checking for error.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking kvm.h usability... no
checking kvm.h presence... no
checking for kvm.h... no
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking sys/syscall.h usability... yes
checking sys/syscall.h presence... yes
checking for sys/syscall.h... yes
checking linux/fiemap.h usability... yes
checking linux/fiemap.h presence... yes
checking for linux/fiemap.h... yes
checking whether TIOCNOTTY is defined in sys/ioctl.h... yes
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working volatile... yes
checking whether compiler supports C99 features... yes
checking for mode_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for ptrdiff_t... yes
checking size of unsigned int... 4
checking size of unsigned long... 4
checking for unistd.h... (cached) yes
checking whether sys_siglist is declared... yes
checking whether compiler supports __attribute__... yes
checking for va_copy... yes
checking for C99 snprintf functions... yes
checking whether sync is asynchronous... no
checking whether offsetof is declared... yes
checking whether WCOREDUMP is declared... yes
checking for getopt... yes
checking for getopt_long... yes
checking for obstack_free... yes
checking for strnlen... yes
checking for strerror... yes
checking for strsignal... yes
checking for scandir... yes
checking for alphasort... yes
checking for unsetenv... yes
checking for strtoul... yes
checking for isascii... yes
checking for bcopy... yes
checking for memcpy... yes
checking for lchown... yes
checking for setsid... yes
checking for getdtablesize... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating dpkg-deb/Makefile
config.status: creating dpkg-split/Makefile
config.status: creating dselect/Makefile
config.status: creating dselect/methods/Makefile
config.status: creating dselect/po/Makefile.in
config.status: creating lib/Makefile
config.status: creating lib/compat/Makefile
config.status: creating lib/dpkg/Makefile
config.status: creating lib/dpkg/test/Makefile
config.status: creating doc/Doxyfile
config.status: creating man/Makefile
config.status: creating po/Makefile.in
config.status: creating scripts/Makefile
config.status: creating scripts/po/Makefile.in
config.status: creating src/Makefile
config.status: creating utils/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating dselect/po/POTFILES
config.status: creating dselect/po/Makefile
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: creating scripts/po/POTFILES
config.status: creating scripts/po/Makefile
```

make
```
make  all-recursive
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5'
Making all in lib
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
Making all in compat
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/compat'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/compat'
Making all in dpkg
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
Making all in test
make[4]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg/test'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg/test'
make[4]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
Making all in dpkg-deb
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-deb'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-deb'
Making all in dpkg-split
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-split'
  GEN    mksplit
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-split'
Making all in src
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/src'
Making all in utils
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/utils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/utils'
Making all in dselect
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
Making all in methods
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/methods'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/methods'
Making all in po
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/po'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/po'
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
  CXX    basecmds.o
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5'
```

make install
```
Making install in lib
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
Making install in compat
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/compat'
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/compat'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/compat'
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/compat'
Making install in dpkg
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
Making install in test
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg/test'
make[4]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg/test'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg/test'
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg/test'
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[4]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib/dpkg'
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/lib'
Making install in dpkg-deb
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-deb'
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-deb'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c dpkg-deb '/usr/local/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-deb'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-deb'
Making install in dpkg-split
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-split'
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-split'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c dpkg-split '/usr/local/bin'
test -z "/usr/local/lib/dpkg" || /bin/mkdir -p "/usr/local/lib/dpkg"
 /usr/bin/install -c mksplit '/usr/local/lib/dpkg'
/bin/mkdir -p /usr/local/var/dpkg/parts
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-split'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dpkg-split'
Making install in src
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/src'
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c dpkg dpkg-query dpkg-statoverride dpkg-trigger '/usr/local/bin'
/bin/mkdir -p /usr/local/etc/dpkg/dpkg.cfg.d
/bin/mkdir -p /usr/local/var/dpkg/alternatives
/bin/mkdir -p /usr/local/var/dpkg/info
/bin/mkdir -p /usr/local/var/dpkg/updates
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/src'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/src'
Making install in utils
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/utils'
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/utils'
test -z "/usr/local/sbin" || /bin/mkdir -p "/usr/local/sbin"
  /usr/bin/install -c dpkg-install-info '/usr/local/sbin/./install-info'
  /usr/bin/install -c start-stop-daemon '/usr/local/sbin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/utils'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/utils'
Making install in dselect
make[1]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
Making install in methods
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/methods'
make[3]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/methods'
make[3]: Nothing to be done for `install-exec-am'.
/bin/mkdir -p /usr/local/var/dpkg/methods/mnt
/bin/mkdir -p /usr/local/var/dpkg/methods/disk
/bin/mkdir -p /usr/local/var/dpkg/methods/floppy
/bin/mkdir -p /usr/local/var/dpkg/methods/ftp
/bin/mkdir -p /usr/local/var/dpkg/methods/multicd
test -z "/usr/local/lib/dpkg/methods" || /bin/mkdir -p "/usr/local/lib/dpkg/methods"
/bin/mkdir -p '/usr/local/lib/dpkg/methods/multicd'
 /usr/bin/install -c -m 644  multicd/names multicd/desc.multi_cd multicd/desc.multi_mount multicd/desc.multi_nfs '/usr/local/lib/dpkg/methods/multicd'
/bin/mkdir -p '/usr/local/lib/dpkg/methods/disk'
 /usr/bin/install -c -m 644  disk/names disk/desc.cdrom disk/desc.nfs disk/desc.harddisk disk/desc.mounted '/usr/local/lib/dpkg/methods/disk'
/bin/mkdir -p '/usr/local/lib/dpkg/methods/ftp'
 /usr/bin/install -c -m 644  ftp/names ftp/desc.ftp ftp/README.mirrors.txt '/usr/local/lib/dpkg/methods/ftp'
/bin/mkdir -p '/usr/local/lib/dpkg/methods/floppy'
 /usr/bin/install -c -m 644  floppy/names floppy/desc.floppy '/usr/local/lib/dpkg/methods/floppy'
test -z "/usr/local/lib/dpkg/methods" || /bin/mkdir -p "/usr/local/lib/dpkg/methods"
 /bin/mkdir -p '/usr/local/lib/dpkg/methods/disk/'
 /bin/mkdir -p '/usr/local/lib/dpkg/methods/floppy/'
 /bin/mkdir -p '/usr/local/lib/dpkg/methods/ftp/'
 /bin/mkdir -p '/usr/local/lib/dpkg/methods/multicd/'
 /usr/bin/install -c ftp/setup ftp/update ftp/install '/usr/local/lib/dpkg/methods/ftp/'
 /usr/bin/install -c disk/setup disk/update disk/install '/usr/local/lib/dpkg/methods/disk/'
 /usr/bin/install -c multicd/setup multicd/update multicd/install '/usr/local/lib/dpkg/methods/multicd/'
 /usr/bin/install -c floppy/setup floppy/update floppy/install '/usr/local/lib/dpkg/methods/floppy/'
test -z "/usr/local/share/perl5" || /bin/mkdir -p "/usr/local/share/perl5"
/bin/mkdir -p '/usr/local/share/perl5/Debian/Dselect'
 /usr/bin/install -c -m 644  Debian/Dselect/Ftp.pm '/usr/local/share/perl5/Debian/Dselect'
make[3]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/methods'
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/methods'
Making install in po
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/po'
/bin/mkdir -p /usr/local/share
installing bs.gmo as /usr/local/share/locale/bs/LC_MESSAGES/dselect.mo
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/dselect.mo
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/dselect.mo
installing da.gmo as /usr/local/share/locale/da/LC_MESSAGES/dselect.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/dselect.mo
installing el.gmo as /usr/local/share/locale/el/LC_MESSAGES/dselect.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/dselect.mo
installing et.gmo as /usr/local/share/locale/et/LC_MESSAGES/dselect.mo
installing eu.gmo as /usr/local/share/locale/eu/LC_MESSAGES/dselect.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/dselect.mo
installing gl.gmo as /usr/local/share/locale/gl/LC_MESSAGES/dselect.mo
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/dselect.mo
installing id.gmo as /usr/local/share/locale/id/LC_MESSAGES/dselect.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/dselect.mo
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/dselect.mo
installing ko.gmo as /usr/local/share/locale/ko/LC_MESSAGES/dselect.mo
installing nb.gmo as /usr/local/share/locale/nb/LC_MESSAGES/dselect.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/dselect.mo
installing nn.gmo as /usr/local/share/locale/nn/LC_MESSAGES/dselect.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/dselect.mo
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/dselect.mo
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/dselect.mo
installing ro.gmo as /usr/local/share/locale/ro/LC_MESSAGES/dselect.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/dselect.mo
installing sk.gmo as /usr/local/share/locale/sk/LC_MESSAGES/dselect.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/dselect.mo
installing tl.gmo as /usr/local/share/locale/tl/LC_MESSAGES/dselect.mo
installing vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/dselect.mo
installing zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/dselect.mo
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/dselect.mo
if test "dpkg" = "gettext-tools"; then \
      /bin/mkdir -p /usr/local/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin    Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/local/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/local/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect/po'
make[2]: Entering directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
  CXX    basecmds.o
make[2]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
make[1]: Leaving directory `/home/static/Downloads/dpkg/dpkg-1.15.5.6ubuntu4.5/dselect'
```

Thanks for your help so far, it is greatly appreciated. 

Thanks
SlashWannabe94

---

### Post by drs305 on 2011-10-08
I tried renaming /usr/bin/dpkg and the 'apt-get install' command still worked on my system. The *dpkg* errors you get when you try to install something may be related to one of the other packages it's trying to install.

*dpkg* should be in the 'main' repository. If APT is still working, try installing it via:```

sudo apt-get install dpkg
```
Run the above just to see if you can install dpkg normally - an easy thing to try and it may even work.

---

### Post by slashwannabe94 on 2011-10-09
> **drs305 said:**
> I tried renaming /usr/bin/dpkg and the 'apt-get install' command still worked on my system. The *dpkg* errors you get when you try to install something may be related to one of the other packages it's trying to install.

*dpkg* should be in the 'main' repository. If APT is still working, try installing it via:```

sudo apt-get install dpkg
```Run the above just to see if you can install dpkg normally - an easy thing to try and it may even work.

Nope when i run ```
sudo apt-get install dpkg
``` i get the error code: 
```
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

Thanks,
SlashWannabe94

---

### Post by matt_symes on 2011-10-09
Hi

I though apt was a front end to dpkg. You may have problems here.

Can you manually extract the deb file and manually install it ?

What other files are you missing from dpkg ?

What's the output of  

```
ls /usr/bin/dpkg*
```Post back results.

Kind regards

---

### Post by drs305 on 2011-10-09
> **matt_symes said:**
> Hi

I though apt was a front end to dpkg. You may have problems here.

I suspected as much but was surprised when APT still seemed to run after I'd removed the dpkg file...  Perhaps it would have failed if I'd rebooted.

---

### Post by slashwannabe94 on 2011-10-09
> **matt_symes said:**
> Hi

I though apt was a front end to dpkg. You may have problems here.

Can you manually extract the deb file and manually install it ?

What other files are you missing from dpkg ?

What's the output of  

```
ls /usr/bin/dpkg*
```Post back results.

Kind regards

ls /usr/bin/dpkg*

```
/usr/bin/dpkg-architecture    /usr/bin/dpkg-deb         /usr/bin/dpkg-genchanges  /usr/bin/dpkg-name         /usr/bin/dpkg-scanpackages  /usr/bin/dpkg-source     /usr/bin/dpkg-trigger
/usr/bin/dpkg-buildpackage    /usr/bin/dpkg-distaddfile  /usr/bin/dpkg-gencontrol  /usr/bin/dpkg-parsechangelog  /usr/bin/dpkg-scansources   /usr/bin/dpkg-split     /usr/bin/dpkg-vendor
/usr/bin/dpkg-checkbuilddeps  /usr/bin/dpkg-divert     /usr/bin/dpkg-gensymbols  /usr/bin/dpkg-query         /usr/bin/dpkg-shlibdeps     /usr/bin/dpkg-statoverride

```

That is the outpiut of 'ls /usr/bin/dpkg*'

Thanks,
SlashWannabe94

---

### Post by matt_symes on 2011-10-09
Hi

> That is the outpiut of 'ls /usr/bin/dpkg*'

The only executable you are missing is dkpg from that list.

Let's have a quick look elsewhere as well.

Can you also post the output of

```
ls /var/lib/dpkg
```

Kind regards

---

### Post by slashwannabe94 on 2011-10-09
It's all good now people. I Can install and remove as i wish. I found an old post about this problem and tried the following commands. They worked. 

```

mkdir /tmp/dpkg
cd /tmp/dpkg
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_i386.deb
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
sudo cp ./usr/bin/dpkg /usr/bin/
sudo apt-get update
sudo apt-get install --reinstall dpkg

```Thanks, 
SlashWannabe94

---

### Post by matt_symes on 2011-10-09
Hi

> **slashwannabe94 said:**
> It's all good now people. I Can install and remove as i wish. I found an old post about this problem and tried the following commands. They worked. 

```

mkdir /tmp/dpkg
cd /tmp/dpkg
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_i386.deb
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
sudo cp ./usr/bin/dpkg /usr/bin/
sudo apt-get update
sudo apt-get install --reinstall dpkg

```Thanks, 
SlashWannabe94

Installing after extracting from the .deb is easier than building from source. You may not have needed the last step depending on whether it was just the dpkg executable missing but it is better to be safe than sorry.

I am happy it worked out for you :D

Kind regards

---

### Post by isamwiza on 2012-06-07
i solve it by following steps:
1/ login as root
2/ cd  /usr/bin
3/ chmod 777 dpkg
4/ apt-get update

---

