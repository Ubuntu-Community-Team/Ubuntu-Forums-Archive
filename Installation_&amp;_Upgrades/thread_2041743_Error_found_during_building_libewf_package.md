---
title: "Error found during building libewf package"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by oscarchoi on 2012-08-13
Below is the stdout and stderr during building libewf package

dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package libewf
dpkg-buildpackage: source version 20120809-1
dpkg-buildpackage: source changed by Joachim Metz <joachim.metz@gmail.com>
 dpkg-source --before-build libewf-20120809
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh  clean
   dh_testdir
   dh_auto_clean
   dh_clean
 dpkg-source -b libewf-20120809
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: info: using source format `1.0'
dpkg-source: info: building libewf in libewf_20120809-1.tar.gz
dpkg-source: info: building libewf in libewf_20120809-1.dsc
 debian/rules build
dh  build
   dh_testdir
   debian/rules override_dh_auto_configure
make[1]: Entering directory `/tmp/libewf-20120809'
dh_auto_configure -- --enable-python
configure: WARNING: unrecognized options: --disable-maintainer-mode
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking whether make sets $(MAKE)... (cached) yes
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 805306365
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... dlltool
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for pkg-config... /usr/bin/pkg-config
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for an ANSI C-conforming const... yes
checking for working volatile... yes
checking whether to enable enable WINAPI support for cross-compilation... (cached) auto-detect
checking whether to enable enable wide character type support... (cached) no
checking for sys/types.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for mode_t... yes
checking for off_t... yes
checking for size_t... yes
checking for size32_t... no
checking for ssize32_t... no
checking for size64_t... no
checking for ssize64_t... no
checking for off64_t... no
checking for ssize_t... yes
checking for u64... no
checking size of off_t... 8
checking size of size_t... 4
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for fclose... yes
checking for feof... yes
checking for fgets... yes
checking for fopen... yes
checking for fread... yes
checking for fseeko... yes
checking for fseeko64... yes
checking for fwrite... yes
checking for vfprintf... yes
checking for free... yes
checking for malloc... yes
checking for memcmp... yes
checking for memcpy... yes
checking for memset... yes
checking for realloc... yes
checking whether printf supports the conversion specifier "%jd"... yes
checking whether printf supports the conversion specifier "%zd"... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to use search for libcstring in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcstring... no
checking libcstring.h usability... no
checking libcstring.h presence... no
checking for libcstring.h... no
checking for libcstring_get_version in -lcstring... no
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking wctype.h usability... yes
checking wctype.h presence... yes
checking for wctype.h... yes
checking for fgets... (cached) yes
checking for memchr... yes
checking for memcmp... (cached) yes
checking for memcpy... (cached) yes
checking for memrchr... yes
checking for snprintf... yes
checking for sscanf... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strlen... yes
checking for strncasecmp... yes
checking for strncmp... yes
checking for strncpy... yes
checking for strrchr... yes
checking for strstr... yes
checking for vsnprintf... yes
checking whether memrchr is declared... no
checking whether to use search for libcerror in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcerror... no
checking libcerror.h usability... no
checking libcerror.h presence... no
checking for libcerror.h... no
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking varargs.h usability... no
checking varargs.h presence... no
checking for varargs.h... no
checking whether strerror_r is declared... yes
checking for strerror_r... yes
checking whether strerror_r returns char *... no
checking whether to use search for libclocale in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libclocale... no
checking libclocale.h usability... no
checking libclocale.h presence... no
checking for libclocale.h... no
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for getenv... yes
checking for localeconv... yes
checking for setlocale... yes
checking for nl_langinfo... yes
checking for nl_langinfo CODESET support... yes
checking whether to use search for libcnotify in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcnotify... no
checking libcnotify.h usability... no
checking libcnotify.h presence... no
checking for libcnotify.h... no
checking for stdarg.h... (cached) yes
checking for varargs.h... (cached) no
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking whether to use search for libcsplit in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcsplit... no
checking libcsplit.h usability... no
checking libcsplit.h presence... no
checking for libcsplit.h... no
checking whether to use search for libuna in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libuna... no
checking libuna.h usability... no
checking libuna.h presence... no
checking for libuna.h... no
checking whether to use search for libcfile in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcfile... no
checking libcfile.h usability... no
checking libcfile.h presence... no
checking for libcfile.h... no
checking for errno.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking for close... yes
checking for fstat... yes
checking for ftruncate... yes
checking for lseek... yes
checking for open... yes
checking for read... yes
checking for write... yes
checking for fclose... (cached) yes
checking for feof... (cached) yes
checking for fopen... (cached) yes
checking for fread... (cached) yes
checking for fseeko... (cached) yes
checking for fseeko64... (cached) yes
checking for ftello... yes
checking for ftello64... yes
checking for fwrite... (cached) yes
checking for stat... yes
checking whether to use search for libcpath in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcpath... no
checking libcpath.h usability... no
checking libcpath.h presence... no
checking for libcpath.h... no
checking for errno.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking sys/syslimits.h usability... no
checking sys/syslimits.h presence... no
checking for sys/syslimits.h... no
checking for chdir... yes
checking for getcwd... yes
checking for mkdir... yes
checking how to use mkdir... with additional mode argument
checking whether to use search for libbfio in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libbfio... no
checking libbfio.h usability... no
checking libbfio.h presence... no
checking for libbfio.h... no
checking whether to use search for libfvalue in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libfvalue... no
checking libfvalue.h usability... no
checking libfvalue.h presence... no
checking for libfvalue.h... no
checking whether to use search for libmfcache in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libmfcache... no
checking libmfcache.h usability... no
checking libmfcache.h presence... no
checking for libmfcache.h... no
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether time.h and sys/time.h may both be included... yes
checking for time... yes
checking whether to use search for libmfdata in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libmfdata... no
checking libmfdata.h usability... no
checking libmfdata.h presence... no
checking for libmfdata.h... no
checking whether to use search for zlib in includedir and libdir or in the specified DIR, or no if not to use zlib... (cached) auto-detect
checking whether to use specify which alder32 implementation to use, options: 'auto-detect', 'zlib' or 'local'... (cached) auto-detect
checking for zlib... no
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking whether to use search for bzip2 in includedir and libdir or in the specified DIR, or no if not to use bzip2... (cached) auto-detect
checking for bzip2... no
checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no
checking whether to use search for libhmac in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libhmac... no
checking libhmac.h usability... no
checking libhmac.h presence... no
checking for libhmac.h... no
checking whether to use search for openssl in includedir and libdir or in the specified DIR, or no if not to use openssl... (cached) auto-detect
checking for openssl... no
checking openssl/opensslv.h usability... no
checking openssl/opensslv.h presence... no
checking for openssl/opensslv.h... no
checking openssl/evp.h usability... no
checking openssl/evp.h presence... no
checking for openssl/evp.h... no
checking whether to use search for libcaes in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcaes... no
checking libcaes.h usability... no
checking libcaes.h presence... no
checking for libcaes.h... no
checking whether to use search for openssl in includedir and libdir or in the specified DIR, or no if not to use openssl... (cached) auto-detect
checking for openssl... no
checking for openssl/opensslv.h... (cached) no
checking for openssl/evp.h... (cached) no
checking whether struct tm is in sys/time.h or time.h... (cached) time.h
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for localtime... yes
checking for localtime_r... yes
checking for mktime... yes
checking for bindtextdomain... yes
checking whether to use search for libcsystem in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libcsystem... no
checking libcsystem.h usability... no
checking libcsystem.h presence... no
checking for libcsystem.h... no
checking whether struct tm is in sys/time.h or time.h... (cached) time.h
checking for errno.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking glob.h usability... yes
checking glob.h presence... yes
checking for glob.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking for close... (cached) yes
checking for fstat... (cached) yes
checking for ftruncate... (cached) yes
checking for lseek... (cached) yes
checking for open... (cached) yes
checking for read... (cached) yes
checking for stat... (cached) yes
checking for write... (cached) yes
checking for localtime... (cached) yes
checking for localtime_r... (cached) yes
checking for mktime... (cached) yes
checking for ctime_r... yes
checking how to use ctime_r... with two arguments
checking for gmtime... yes
checking for gmtime_r... yes
checking for time... (cached) yes
checking for getopt... yes
checking for setvbuf... yes
checking for bindtextdomain... (cached) yes
checking for textdomain... yes
checking whether to use search for libuuid in includedir and libdir or in the specified DIR, or no if not to use libuuid... (cached) auto-detect
checking for uuid... no
checking uuid/uuid.h usability... no
checking uuid/uuid.h presence... no
checking for uuid/uuid.h... no
checking for flex... no
checking for lex... no
checking whether to use search for libodraw in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libodraw... no
checking libodraw.h usability... no
checking libodraw.h presence... no
checking for libodraw.h... no
checking for bison... no
checking for byacc... no
checking whether to use search for libmsdev in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libsmdev... no
checking libsmdev.h usability... no
checking libsmdev.h presence... no
checking for libsmdev.h... no
checking for errno.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for unistd.h... (cached) yes
checking cygwin/fs.h usability... no
checking cygwin/fs.h presence... no
checking for cygwin/fs.h... no
checking linux/fs.h usability... yes
checking linux/fs.h presence... yes
checking for linux/fs.h... yes
checking sys/disk.h usability... no
checking sys/disk.h presence... no
checking for sys/disk.h... no
checking sys/disklabel.h usability... no
checking sys/disklabel.h presence... no
checking for sys/disklabel.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking cygwin/hdreg.h usability... no
checking cygwin/hdreg.h presence... no
checking for cygwin/hdreg.h... no
checking linux/hdreg.h usability... yes
checking linux/hdreg.h presence... yes
checking for linux/hdreg.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking scsi/scsi_ioctl.h usability... yes
checking scsi/scsi_ioctl.h presence... yes
checking for scsi/scsi_ioctl.h... yes
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking linux/usbdevice_fs.h usability... yes
checking linux/usbdevice_fs.h presence... yes
checking for linux/usbdevice_fs.h... yes
checking linux/usb/ch9.h usability... yes
checking linux/usb/ch9.h presence... yes
checking for linux/usb/ch9.h... yes
checking for close... (cached) yes
checking for fstat... (cached) yes
checking for ftruncate... (cached) yes
checking for lseek... (cached) yes
checking for open... (cached) yes
checking for read... (cached) yes
checking for stat... (cached) yes
checking for write... (cached) yes
checking for posix_fadvise... yes
checking whether posix_fadvise can be linked... yes
checking whether strerror_r is declared... (cached) yes
checking for strerror_r... (cached) yes
checking whether strerror_r returns char *... (cached) no
checking whether to use search for libmsraw in includedir and libdir or in the specified DIR, or no if to use local version... (cached) auto-detect
checking for libsmraw... no
checking libsmraw.h usability... no
checking libsmraw.h presence... no
checking for libsmraw.h... no
checking whether to use search for libfuse in includedir and libdir or in the specified DIR, or no if not to use libfuse... (cached) auto-detect
checking for fuse... no
checking fuse.h usability... no
checking fuse.h presence... no
checking for fuse.h... no
checking fuse.h usability... no
checking fuse.h presence... no
checking for fuse.h... no
checking osxfuse/fuse.h usability... no
checking osxfuse/fuse.h presence... no
checking for osxfuse/fuse.h... no
checking osxfuse/fuse.h usability... no
checking osxfuse/fuse.h presence... no
checking for osxfuse/fuse.h... no
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for getegid... yes
checking for geteuid... yes
checking for getrlimit... yes
checking for getuid... yes
checking for uname... yes
checking whether to enable build static executables (binaries)... (cached) no
checking whether to enable use libewf's low level read and write functions in the ewftools... (cached) no
checking whether to enable enable verbose output... (cached) no
checking whether to enable enable debug output... (cached) no
checking whether to enable build Python bindings... (cached) yes
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for Python include path... /usr/include/python2.7
configure: error: Missing Python include file
==> config.log <==
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by libewf configure 20120809, which was
generated by GNU Autoconf 2.68.  Invocation command line was

  $ ./configure --build=i686-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/libewf --disable-maintainer-mode --disable-dependency-tracking --enable-python

## --------- ##
## Platform. ##
## --------- ##

hostname = oscar-ThinkPad-T500
uname -m = i686
uname -r = 3.2.0-29-generic-pae
uname -s = Linux
uname -v = #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:3088: checking for a BSD-compatible install
configure:3156: result: /usr/bin/install -c
configure:3167: checking whether build environment is sane
configure:3217: result: yes
configure:3358: checking for a thread-safe mkdir -p
configure:3397: result: /bin/mkdir -p
configure:3410: checking for gawk
configure:3440: result: no
configure:3410: checking for mawk
configure:3426: found /usr/bin/mawk
configure:3437: result: mawk
configure:3448: checking whether make sets $(MAKE)
configure:3470: result: yes
configure:3557: checking build system type
configure:3571: result: i686-pc-linux-gnu
configure:3591: checking host system type
configure:3604: result: i686-pc-linux-gnu
configure:3637: checking for style of include used by make
configure:3665: result: GNU
configure:3735: checking for gcc
configure:3751: found /usr/bin/gcc
configure:3762: result: gcc
configure:3991: checking for C compiler version
configure:4000: gcc --version >&5
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4011: $? = 0
configure:4000: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
configure:4011: $? = 0
configure:4000: gcc -V >&5
gcc: error: unrecognized option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:4011: $? = 4
configure:4000: gcc -qversion >&5
gcc: error: unrecognized option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:4011: $? = 4
configure:4031: checking whether the C compiler works
configure:4053: gcc -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:4057: $? = 0
configure:4105: result: yes
configure:4108: checking for C compiler default output file name
configure:4110: result: a.out
configure:4116: checking for suffix of executables
configure:4123: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:4127: $? = 0
configure:4149: result: 
configure:4171: checking whether we are cross compiling
configure:4179: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:4183: $? = 0
configure:4190: ./conftest
configure:4194: $? = 0
configure:4209: result: no
configure:4214: checking for suffix of object files
configure:4236: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:4240: $? = 0
configure:4261: result: o
configure:4265: checking whether we are using the GNU C compiler
configure:4284: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:4284: $? = 0
configure:4293: result: yes
configure:4302: checking whether gcc accepts -g
configure:4322: gcc -c -g -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:4322: $? = 0
configure:4363: result: yes
configure:4380: checking for gcc option to accept ISO C89
configure:4444: gcc  -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:4444: $? = 0
configure:4457: result: none needed
configure:4479: checking dependency style of gcc
configure:4589: result: none
configure:4612: checking for special C compiler options needed for large files
configure:4657: result: no
configure:4663: checking for _FILE_OFFSET_BITS value needed for large files
configure:4688: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:17:3: warning: left shift count >= width of type [enabled by default]
conftest.c:17:3: warning: left shift count >= width of type [enabled by default]
conftest.c:18:10: warning: left shift count >= width of type [enabled by default]
conftest.c:18:10: warning: left shift count >= width of type [enabled by default]
conftest.c:17:7: error: size of array 'off_t_is_large' is negative
conftest.c:19:9: warning: variably modified 'off_t_is_large' at file scope [enabled by default]
configure:4688: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| /* end confdefs.h.  */
| #include <sys/types.h>
|  /* Check that off_t can represent 2**63 - 1 correctly.
|     We can't simply define LARGE_OFF_T to be 9223372036854775807,
|     since some C++ compilers masquerading as C compilers
|     incorrectly reject 9223372036854775807.  */
| #define LARGE_OFF_T (((off_t) 1 << 62) - 1 + ((off_t) 1 << 62))
|   int off_t_is_large[(LARGE_OFF_T % 2147483629 == 721
|                && LARGE_OFF_T % 2147483647 == 1)
|               ? 1 : -1];
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:4712: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:4712: $? = 0
configure:4720: result: 64
configure:5156: checking for gcc
configure:5183: result: gcc
configure:5412: checking for C compiler version
configure:5421: gcc --version >&5
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:5432: $? = 0
configure:5421: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
configure:5432: $? = 0
configure:5421: gcc -V >&5
gcc: error: unrecognized option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:5432: $? = 4
configure:5421: gcc -qversion >&5
gcc: error: unrecognized option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:5432: $? = 4
configure:5436: checking whether we are using the GNU C compiler
configure:5464: result: yes
configure:5473: checking whether gcc accepts -g
configure:5534: result: yes
configure:5551: checking for gcc option to accept ISO C89
configure:5628: result: none needed
configure:5650: checking dependency style of gcc
configure:5760: result: none
configure:5780: checking how to run the C preprocessor
configure:5811: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:5811: $? = 0
configure:5825: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:12:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:5825: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5850: result: gcc -E
configure:5870: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:5870: $? = 0
configure:5884: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:12:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:5884: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5913: checking for grep that handles long lines and -e
configure:5971: result: /bin/grep
configure:5976: checking for egrep
configure:6038: result: /bin/grep -E
configure:6044: checking whether gcc needs -traditional
configure:6078: result: no
configure:6085: checking whether make sets $(MAKE)
configure:6107: result: yes
configure:6164: checking how to print strings
configure:6191: result: printf
configure:6212: checking for a sed that does not truncate output
configure:6276: result: /bin/sed
configure:6294: checking for fgrep
configure:6356: result: /bin/grep -F
configure:6391: checking for ld used by gcc
configure:6458: result: /usr/bin/ld
configure:6465: checking if the linker (/usr/bin/ld) is GNU ld
configure:6480: result: yes
configure:6492: checking for BSD- or MS-compatible name lister (nm)
configure:6541: result: /usr/bin/nm -B
configure:6671: checking the name lister (/usr/bin/nm -B) interface
configure:6678: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:6681: /usr/bin/nm -B "conftest.o"
configure:6684: output
00000000 B some_variable
configure:6691: result: BSD nm
configure:6694: checking whether ln -s works
configure:6698: result: yes
configure:6706: checking the maximum length of command line arguments
configure:6831: result: 805306365
configure:6848: checking whether the shell understands some XSI constructs
configure:6858: result: yes
configure:6862: checking whether the shell understands "+="
configure:6868: result: yes
configure:6903: checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format
configure:6943: result: func_convert_file_noop
configure:6950: checking how to convert i686-pc-linux-gnu file names to toolchain format
configure:6970: result: func_convert_file_noop
configure:6977: checking for /usr/bin/ld option to reload object files
configure:6984: result: -r
configure:7058: checking for objdump
configure:7085: result: objdump
configure:7114: checking how to recognize dependent libraries
configure:7316: result: pass_all
configure:7401: checking for dlltool
configure:7428: result: dlltool
configure:7458: checking how to associate runtime and link libraries
configure:7485: result: printf %s\n
configure:7545: checking for ar
configure:7561: found /usr/bin/ar
configure:7572: result: ar
configure:7609: checking for archiver @FILE support
configure:7626: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:7626: $? = 0
configure:7629: ar cru libconftest.a @conftest.lst >&5
configure:7632: $? = 0
configure:7637: ar cru libconftest.a @conftest.lst >&5
ar: conftest.o: No such file or directory
configure:7640: $? = 1
configure:7652: result: @
configure:7710: checking for strip
configure:7726: found /usr/bin/strip
configure:7737: result: strip
configure:7809: checking for ranlib
configure:7825: found /usr/bin/ranlib
configure:7836: result: ranlib
configure:7938: checking command to parse /usr/bin/nm -B output from gcc object
configure:8057: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:8060: $? = 0
configure:8064: /usr/bin/nm -B conftest.o \| sed -n -e 's/^.*[ ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ ][ ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | sed '/ __gnu_lto/d' \> conftest.nm
configure:8067: $? = 0
configure:8133: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c conftstm.o >&5
configure:8136: $? = 0
configure:8174: result: ok
configure:8211: checking for sysroot
configure:8241: result: no
configure:8484: checking for mt
configure:8500: found /bin/mt
configure:8511: result: mt
configure:8534: checking if mt is a manifest tool
configure:8540: mt '-?'
configure:8548: result: no
configure:9175: checking for ANSI C header files
configure:9195: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9195: $? = 0
configure:9268: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:9268: $? = 0
configure:9268: ./conftest
configure:9268: $? = 0
configure:9279: result: yes
configure:9292: checking for sys/types.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for sys/stat.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for stdlib.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for string.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for memory.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for strings.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for inttypes.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for stdint.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9292: checking for unistd.h
configure:9292: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9292: $? = 0
configure:9292: result: yes
configure:9306: checking for dlfcn.h
configure:9306: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:9306: $? = 0
configure:9306: result: yes
configure:9491: checking for objdir
configure:9506: result: .libs
configure:9777: checking if gcc supports -fno-rtti -fno-exceptions
configure:9795: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option '-fno-rtti' is valid for C++/ObjC++ but not for C [enabled by default]
configure:9799: $? = 0
configure:9812: result: no
configure:10122: checking for gcc option to produce PIC
configure:10129: result: -fPIC -DPIC
configure:10137: checking if gcc PIC flag -fPIC -DPIC works
configure:10155: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -fPIC -DPIC -DPIC conftest.c >&5
configure:10159: $? = 0
configure:10172: result: yes
configure:10201: checking if gcc static flag -static works
configure:10229: result: yes
configure:10244: checking if gcc supports -c -o file.o
configure:10265: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -o out/conftest2.o conftest.c >&5
configure:10269: $? = 0
configure:10291: result: yes
configure:10299: checking if gcc supports -c -o file.o
configure:10346: result: yes
configure:10379: checking whether the gcc linker (/usr/bin/ld) supports shared libraries
configure:11537: result: yes
configure:11574: checking whether -lc should be explicitly linked in
configure:11582: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:11585: $? = 0
configure:11600: gcc -shared  -fPIC -DPIC conftest.o  -v -Wl,-soname -Wl,conftest -o conftest 2\>\&1 \| /bin/grep  -lc  \>/dev/null 2\>\&1
configure:11603: $? = 0
configure:11617: result: no
configure:11782: checking dynamic linker characteristics
configure:12296: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-rpath -Wl,/foo conftest.c  >&5
configure:12296: $? = 0
configure:12522: result: GNU/Linux ld.so
configure:12629: checking how to hardcode library paths into programs
configure:12654: result: immediate
configure:13194: checking whether stripping libraries is possible
configure:13199: result: yes
configure:13234: checking if libtool supports shared libraries
configure:13236: result: yes
configure:13239: checking whether to build shared libraries
configure:13260: result: yes
configure:13263: checking whether to build static libraries
configure:13267: result: yes
configure:13306: checking for pkg-config
configure:13324: found /usr/bin/pkg-config
configure:13336: result: /usr/bin/pkg-config
configure:13346: checking whether NLS is requested
configure:13355: result: yes
configure:13396: checking for msgfmt
configure: trying /usr/bin/msgfmt...
0 translated messages.
configure:13428: result: /usr/bin/msgfmt
configure:13437: checking for gmsgfmt
configure:13468: result: /usr/bin/msgfmt
configure:13519: checking for xgettext
configure: trying /usr/bin/xgettext...
/usr/bin/xgettext: warning: file `/dev/null' extension `' is unknown; will try C
configure:13551: result: /usr/bin/xgettext
configure:13597: checking for msgmerge
configure: trying /usr/bin/msgmerge...
configure:13628: result: /usr/bin/msgmerge
configure:13685: checking for ld used by GCC
configure:13749: result: /usr/bin/ld
configure:13756: checking if the linker (/usr/bin/ld) is GNU ld
configure:13769: result: yes
configure:13776: checking for shared library run path origin
configure:13789: result: done
configure:14361: checking for CFPreferencesCopyAppValue
configure:14379: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  -Wl,-framework -Wl,CoreFoundation >&5
conftest.c:24:42: fatal error: CoreFoundation/CFPreferences.h: No such file or directory
compilation terminated.
configure:14379: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| /* end confdefs.h.  */
| #include <CoreFoundation/CFPreferences.h>
| int
| main ()
| {
| CFPreferencesCopyAppValue(NULL, NULL)
|   ;
|   return 0;
| }
configure:14388: result: no
configure:14395: checking for CFLocaleCopyCurrent
configure:14413: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  -Wl,-framework -Wl,CoreFoundation >&5
conftest.c:24:37: fatal error: CoreFoundation/CFLocale.h: No such file or directory
compilation terminated.
configure:14413: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| /* end confdefs.h.  */
| #include <CoreFoundation/CFLocale.h>
| int
| main ()
| {
| CFLocaleCopyCurrent();
|   ;
|   return 0;
| }
configure:14422: result: no
configure:14471: checking for GNU gettext in libc
configure:14491: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:14491: $? = 0
configure:14500: result: yes
configure:15291: checking whether to use NLS
configure:15293: result: yes
configure:15296: checking where the gettext function comes from
configure:15307: result: libc
configure:15365: checking for an ANSI C-conforming const
configure:15430: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15430: $? = 0
configure:15437: result: yes
configure:15445: checking for working volatile
configure:15464: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15464: $? = 0
configure:15471: result: yes
configure:15486: checking whether to enable enable WINAPI support for cross-compilation
configure:15493: result: auto-detect
configure:15523: checking whether to enable enable wide character type support
configure:15530: result: no
configure:15555: checking for sys/types.h
configure:15555: result: yes
configure:15555: checking for inttypes.h
configure:15555: result: yes
configure:15555: checking for stdint.h
configure:15555: result: yes
configure:15593: checking for mode_t
configure:15593: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15593: $? = 0
configure:15593: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:21: error: expected expression before ')' token
configure:15593: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof ((mode_t)))
|         return 0;
|   ;
|   return 0;
| }
configure:15593: result: yes
configure:15604: checking for off_t
configure:15604: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15604: $? = 0
configure:15604: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:20: error: expected expression before ')' token
configure:15604: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof ((off_t)))
|         return 0;
|   ;
|   return 0;
| }
configure:15604: result: yes
configure:15615: checking for size_t
configure:15615: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15615: $? = 0
configure:15615: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:21: error: expected expression before ')' token
configure:15615: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof ((size_t)))
|         return 0;
|   ;
|   return 0;
| }
configure:15615: result: yes
configure:15627: checking for size32_t
configure:15627: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:13: error: 'size32_t' undeclared (first use in this function)
conftest.c:66:13: note: each undeclared identifier is reported only once for each function it appears in
configure:15627: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof (size32_t))
|      return 0;
|   ;
|   return 0;
| }
configure:15627: result: no
configure:15638: checking for ssize32_t
configure:15638: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:13: error: 'ssize32_t' undeclared (first use in this function)
conftest.c:66:13: note: each undeclared identifier is reported only once for each function it appears in
configure:15638: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof (ssize32_t))
|      return 0;
|   ;
|   return 0;
| }
configure:15638: result: no
configure:15649: checking for size64_t
configure:15649: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:13: error: 'size64_t' undeclared (first use in this function)
conftest.c:66:13: note: each undeclared identifier is reported only once for each function it appears in
configure:15649: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof (size64_t))
|      return 0;
|   ;
|   return 0;
| }
configure:15649: result: no
configure:15660: checking for ssize64_t
configure:15660: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:13: error: 'ssize64_t' undeclared (first use in this function)
conftest.c:66:13: note: each undeclared identifier is reported only once for each function it appears in
configure:15660: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof (ssize64_t))
|      return 0;
|   ;
|   return 0;
| }
configure:15660: result: no
configure:15671: checking for off64_t
configure:15671: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:13: error: 'off64_t' undeclared (first use in this function)
conftest.c:66:13: note: each undeclared identifier is reported only once for each function it appears in
configure:15671: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof (off64_t))
|      return 0;
|   ;
|   return 0;
| }
configure:15671: result: no
configure:15682: checking for ssize_t
configure:15682: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15682: $? = 0
configure:15682: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:22: error: expected expression before ')' token
configure:15682: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof ((ssize_t)))
|         return 0;
|   ;
|   return 0;
| }
configure:15682: result: yes
configure:15687: checking for u64
configure:15687: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:66:13: error: 'u64' undeclared (first use in this function)
conftest.c:66:13: note: each undeclared identifier is reported only once for each function it appears in
configure:15687: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| if (sizeof (u64))
|      return 0;
|   ;
|   return 0;
| }
configure:15687: result: no
configure:15697: checking size of off_t
configure:15702: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15702: $? = 0
configure:15702: ./conftest
configure:15702: $? = 0
configure:15716: result: 8
configure:15730: checking size of size_t
configure:15735: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15735: $? = 0
configure:15735: ./conftest
configure:15735: $? = 0
configure:15749: result: 4
configure:15848: checking libintl.h usability
configure:15848: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15848: $? = 0
configure:15848: result: yes
configure:15848: checking libintl.h presence
configure:15848: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:15848: $? = 0
configure:15848: result: yes
configure:15848: checking for libintl.h
configure:15848: result: yes
configure:15862: checking limits.h usability
configure:15862: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:15862: $? = 0
configure:15862: result: yes
configure:15862: checking limits.h presence
configure:15862: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:15862: $? = 0
configure:15862: result: yes
configure:15862: checking for limits.h
configure:15862: result: yes
configure:15876: checking for stdlib.h
configure:15876: result: yes
configure:15876: checking for string.h
configure:15876: result: yes
configure:15890: checking for fclose
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for feof
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for fgets
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for fopen
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for fread
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for fseeko
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for fseeko64
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for fwrite
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:66:6: warning: conflicting types for built-in function 'fwrite' [enabled by default]
configure:15890: $? = 0
configure:15890: result: yes
configure:15890: checking for vfprintf
configure:15890: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:67:6: warning: conflicting types for built-in function 'vfprintf' [enabled by default]
configure:15890: $? = 0
configure:15890: result: yes
configure:15990: checking for free
configure:15990: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:68:6: warning: conflicting types for built-in function 'free' [enabled by default]
configure:15990: $? = 0
configure:15990: result: yes
configure:15990: checking for malloc
configure:15990: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:69:6: warning: conflicting types for built-in function 'malloc' [enabled by default]
configure:15990: $? = 0
configure:15990: result: yes
configure:15990: checking for memcmp
configure:15990: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:70:6: warning: conflicting types for built-in function 'memcmp' [enabled by default]
configure:15990: $? = 0
configure:15990: result: yes
configure:15990: checking for memcpy
configure:15990: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:71:6: warning: conflicting types for built-in function 'memcpy' [enabled by default]
configure:15990: $? = 0
configure:15990: result: yes
configure:15990: checking for memset
configure:15990: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:72:6: warning: conflicting types for built-in function 'memset' [enabled by default]
configure:15990: $? = 0
configure:15990: result: yes
configure:15990: checking for realloc
configure:15990: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:73:6: warning: conflicting types for built-in function 'realloc' [enabled by default]
configure:15990: $? = 0
configure:15990: result: yes
configure:16048: checking whether printf supports the conversion specifier "%jd"
configure:16071: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c: In function 'main':
conftest.c:55:1: error: format '%jd' expects a matching 'intmax_t' argument [-Werror=format]
cc1: all warnings being treated as errors
configure:16071: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| /* end confdefs.h.  */
| #include <stdio.h>
| int
| main ()
| {
| printf( "%jd" );
|   ;
|   return 0;
| }
configure:16092: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:16092: $? = 0
configure:16120: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:16120: $? = 0
configure:16120: ./conftest
configure:16120: $? = 0
configure:16141: result: yes
configure:16151: checking whether printf supports the conversion specifier "%zd"
configure:16174: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c: In function 'main':
conftest.c:56:1: error: format '%zd' expects a matching 'signed size_t' argument [-Werror=format]
cc1: all warnings being treated as errors
configure:16174: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| /* end confdefs.h.  */
| #include <stdio.h>
| int
| main ()
| {
| printf( "%zd" );
|   ;
|   return 0;
| }
configure:16195: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:16195: $? = 0
configure:16223: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:16223: $? = 0
configure:16223: ./conftest
configure:16223: $? = 0
configure:16244: result: yes
configure:16309: checking for pkg-config
configure:16327: found /usr/bin/pkg-config
configure:16339: result: /usr/bin/pkg-config
configure:16364: checking pkg-config is at least version 0.9.0
configure:16367: result: yes
configure:16382: checking whether to use search for libcstring in includedir and libdir or in the specified DIR, or no if to use local version
configure:16389: result: auto-detect
configure:16413: checking for libcstring
configure:16420: $PKG_CONFIG --exists --print-errors "libcstring >= 20120425"
Package libcstring was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcstring.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcstring' found
configure:16423: $? = 1
configure:16436: $PKG_CONFIG --exists --print-errors "libcstring >= 20120425"
Package libcstring was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcstring.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcstring' found
configure:16439: $? = 1
configure:16452: result: no
No package 'libcstring' found
configure:16491: checking libcstring.h usability
configure:16491: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:86:24: fatal error: libcstring.h: No such file or directory
compilation terminated.
configure:16491: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcstring.h>
configure:16491: result: no
configure:16491: checking libcstring.h presence
configure:16491: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:53:24: fatal error: libcstring.h: No such file or directory
compilation terminated.
configure:16491: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| /* end confdefs.h.  */
| #include <libcstring.h>
configure:16491: result: no
configure:16491: checking for libcstring.h
configure:16491: result: no
configure:16507: checking for libcstring_get_version in -lcstring
configure:16532: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c -lcstring   >&5
/usr/bin/ld: cannot find -lcstring
collect2: ld returned 1 exit status
configure:16532: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| /* end confdefs.h.  */
| 
| /* Override any GCC internal prototype to avoid an error.
|    Use char because int might match the return type of a GCC
|    builtin and then its argument prototype would still apply.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| char libcstring_get_version ();
| int
| main ()
| {
| return libcstring_get_version ();
|   ;
|   return 0;
| }
configure:16541: result: no
configure:16580: checking for stdlib.h
configure:16580: result: yes
configure:16580: checking for string.h
configure:16580: result: yes
configure:16594: checking wchar.h usability
configure:16594: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:16594: $? = 0
configure:16594: result: yes
configure:16594: checking wchar.h presence
configure:16594: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:16594: $? = 0
configure:16594: result: yes
configure:16594: checking for wchar.h
configure:16594: result: yes
configure:16594: checking wctype.h usability
configure:16594: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:16594: $? = 0
configure:16594: result: yes
configure:16594: checking wctype.h presence
configure:16594: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:16594: $? = 0
configure:16594: result: yes
configure:16594: checking for wctype.h
configure:16594: result: yes
configure:16608: checking for fgets
configure:16608: result: yes
configure:16608: checking for memchr
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:81:6: warning: conflicting types for built-in function 'memchr' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for memcmp
configure:16608: result: yes
configure:16608: checking for memcpy
configure:16608: result: yes
configure:16608: checking for memrchr
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for snprintf
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:85:6: warning: conflicting types for built-in function 'snprintf' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for sscanf
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:86:6: warning: conflicting types for built-in function 'sscanf' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strcasecmp
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:87:6: warning: conflicting types for built-in function 'strcasecmp' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strchr
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:88:6: warning: conflicting types for built-in function 'strchr' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strlen
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:89:6: warning: conflicting types for built-in function 'strlen' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strncasecmp
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:90:6: warning: conflicting types for built-in function 'strncasecmp' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strncmp
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:91:6: warning: conflicting types for built-in function 'strncmp' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strncpy
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:92:6: warning: conflicting types for built-in function 'strncpy' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strrchr
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:93:6: warning: conflicting types for built-in function 'strrchr' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for strstr
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:94:6: warning: conflicting types for built-in function 'strstr' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16608: checking for vsnprintf
configure:16608: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c:95:6: warning: conflicting types for built-in function 'vsnprintf' [enabled by default]
configure:16608: $? = 0
configure:16608: result: yes
configure:16651: checking whether memrchr is declared
configure:16651: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:113:10: error: 'memrchr' undeclared (first use in this function)
conftest.c:113:10: note: each undeclared identifier is reported only once for each function it appears in
configure:16651: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| #ifndef memrchr
| #ifdef __cplusplus
|   (void) memrchr;
| #else
|   (void) memrchr;
| #endif
| #endif
| 
|   ;
|   return 0;
| }
configure:16651: result: no
configure:16860: checking whether to use search for libcerror in includedir and libdir or in the specified DIR, or no if to use local version
configure:16867: result: auto-detect
configure:16888: checking for libcerror
configure:16895: $PKG_CONFIG --exists --print-errors "libcerror >= 20120425"
Package libcerror was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcerror.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcerror' found
configure:16898: $? = 1
configure:16911: $PKG_CONFIG --exists --print-errors "libcerror >= 20120425"
Package libcerror was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcerror.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcerror' found
configure:16914: $? = 1
configure:16927: result: no
No package 'libcerror' found
configure:16964: checking libcerror.h usability
configure:16964: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:108:23: fatal error: libcerror.h: No such file or directory
compilation terminated.
configure:16964: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcerror.h>
configure:16964: result: no
configure:16964: checking libcerror.h presence
configure:16964: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:75:23: fatal error: libcerror.h: No such file or directory
compilation terminated.
configure:16964: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| /* end confdefs.h.  */
| #include <libcerror.h>
configure:16964: result: no
configure:16964: checking for libcerror.h
configure:16964: result: no
configure:17390: checking stdarg.h usability
configure:17390: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:17390: $? = 0
configure:17390: result: yes
configure:17390: checking stdarg.h presence
configure:17390: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:17390: $? = 0
configure:17390: result: yes
configure:17390: checking for stdarg.h
configure:17390: result: yes
configure:17390: checking varargs.h usability
configure:17390: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
In file included from conftest.c:109:0:
/usr/lib/gcc/i686-linux-gnu/4.6/include/varargs.h:4:2: error: #error "GCC no longer implements <varargs.h>."
/usr/lib/gcc/i686-linux-gnu/4.6/include/varargs.h:5:2: error: #error "Revise your code to use <stdarg.h>."
configure:17390: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <varargs.h>
configure:17390: result: no
configure:17390: checking varargs.h presence
configure:17390: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
In file included from conftest.c:76:0:
/usr/lib/gcc/i686-linux-gnu/4.6/include/varargs.h:4:2: error: #error "GCC no longer implements <varargs.h>."
/usr/lib/gcc/i686-linux-gnu/4.6/include/varargs.h:5:2: error: #error "Revise your code to use <stdarg.h>."
configure:17390: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| /* end confdefs.h.  */
| #include <varargs.h>
configure:17390: result: no
configure:17390: checking for varargs.h
configure:17390: result: no
configure:17432: checking whether strerror_r is declared
configure:17432: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:17432: $? = 0
configure:17432: result: yes
configure:17445: checking for strerror_r
configure:17445: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:17445: $? = 0
configure:17445: result: yes
configure:17454: checking whether strerror_r returns char *
configure:17478: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c: In function 'main':
conftest.c:116:13: error: invalid type argument of unary '*' (have 'int')
conftest.c:117:14: warning: initialization makes pointer from integer without a cast [enabled by default]
configure:17478: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| int
| main ()
| {
| 
|       char buf[100];
|       char x = *strerror_r (0, buf, sizeof buf);
|       char *p = strerror_r (0, buf, sizeof buf);
|       return !p || x;
| 
|   ;
|   return 0;
| }
configure:17516: result: no
configure:17603: checking whether to use search for libclocale in includedir and libdir or in the specified DIR, or no if to use local version
configure:17610: result: auto-detect
configure:17631: checking for libclocale
configure:17638: $PKG_CONFIG --exists --print-errors "libclocale >= 20120425"
Package libclocale was not found in the pkg-config search path.
Perhaps you should add the directory containing `libclocale.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libclocale' found
configure:17641: $? = 1
configure:17654: $PKG_CONFIG --exists --print-errors "libclocale >= 20120425"
Package libclocale was not found in the pkg-config search path.
Perhaps you should add the directory containing `libclocale.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libclocale' found
configure:17657: $? = 1
configure:17670: result: no
No package 'libclocale' found
configure:17707: checking libclocale.h usability
configure:17707: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:112:24: fatal error: libclocale.h: No such file or directory
compilation terminated.
configure:17707: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libclocale.h>
configure:17707: result: no
configure:17707: checking libclocale.h presence
configure:17707: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:79:24: fatal error: libclocale.h: No such file or directory
compilation terminated.
configure:17707: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| /* end confdefs.h.  */
| #include <libclocale.h>
configure:17707: result: no
configure:17707: checking for libclocale.h
configure:17707: result: no
configure:18138: checking langinfo.h usability
configure:18138: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:18138: $? = 0
configure:18138: result: yes
configure:18138: checking langinfo.h presence
configure:18138: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:18138: $? = 0
configure:18138: result: yes
configure:18138: checking for langinfo.h
configure:18138: result: yes
configure:18138: checking locale.h usability
configure:18138: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:18138: $? = 0
configure:18138: result: yes
configure:18138: checking locale.h presence
configure:18138: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:18138: $? = 0
configure:18138: result: yes
configure:18138: checking for locale.h
configure:18138: result: yes
configure:18151: checking for getenv
configure:18151: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:18151: $? = 0
configure:18151: result: yes
configure:18172: checking for localeconv
configure:18172: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:18172: $? = 0
configure:18172: result: yes
configure:18194: checking for setlocale
configure:18194: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:18194: $? = 0
configure:18194: result: yes
configure:18214: checking for nl_langinfo
configure:18214: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:18214: $? = 0
configure:18214: result: yes
configure:18225: checking for nl_langinfo CODESET support
configure:18247: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:18247: $? = 0
configure:18261: result: yes
configure:18330: checking whether to use search for libcnotify in includedir and libdir or in the specified DIR, or no if to use local version
configure:18337: result: auto-detect
configure:18358: checking for libcnotify
configure:18365: $PKG_CONFIG --exists --print-errors "libcnotify >= 20120425"
Package libcnotify was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcnotify.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcnotify' found
configure:18368: $? = 1
configure:18381: $PKG_CONFIG --exists --print-errors "libcnotify >= 20120425"
Package libcnotify was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcnotify.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcnotify' found
configure:18384: $? = 1
configure:18397: result: no
No package 'libcnotify' found
configure:18434: checking libcnotify.h usability
configure:18434: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:120:24: fatal error: libcnotify.h: No such file or directory
compilation terminated.
configure:18434: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcnotify.h>
configure:18434: result: no
configure:18434: checking libcnotify.h presence
configure:18434: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:87:24: fatal error: libcnotify.h: No such file or directory
compilation terminated.
configure:18434: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| /* end confdefs.h.  */
| #include <libcnotify.h>
configure:18434: result: no
configure:18434: checking for libcnotify.h
configure:18434: result: no
configure:18819: checking for stdarg.h
configure:18819: result: yes
configure:18819: checking for varargs.h
configure:18819: result: no
configure:18840: checking errno.h usability
configure:18840: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:18840: $? = 0
configure:18840: result: yes
configure:18840: checking errno.h presence
configure:18840: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:18840: $? = 0
configure:18840: result: yes
configure:18840: checking for errno.h
configure:18840: result: yes
configure:18906: checking whether to use search for libcsplit in includedir and libdir or in the specified DIR, or no if to use local version
configure:18913: result: auto-detect
configure:18934: checking for libcsplit
configure:18941: $PKG_CONFIG --exists --print-errors "libcsplit >= 20120701"
Package libcsplit was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcsplit.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcsplit' found
configure:18944: $? = 1
configure:18957: $PKG_CONFIG --exists --print-errors "libcsplit >= 20120701"
Package libcsplit was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcsplit.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcsplit' found
configure:18960: $? = 1
configure:18973: result: no
No package 'libcsplit' found
configure:19010: checking libcsplit.h usability
configure:19010: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:123:23: fatal error: libcsplit.h: No such file or directory
compilation terminated.
configure:19010: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcsplit.h>
configure:19010: result: no
configure:19010: checking libcsplit.h presence
configure:19010: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:90:23: fatal error: libcsplit.h: No such file or directory
compilation terminated.
configure:19010: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| /* end confdefs.h.  */
| #include <libcsplit.h>
configure:19010: result: no
configure:19010: checking for libcsplit.h
configure:19010: result: no
configure:19660: checking whether to use search for libuna in includedir and libdir or in the specified DIR, or no if to use local version
configure:19667: result: auto-detect
configure:19688: checking for libuna
configure:19695: $PKG_CONFIG --exists --print-errors "libuna >= 20120425"
Package libuna was not found in the pkg-config search path.
Perhaps you should add the directory containing `libuna.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libuna' found
configure:19698: $? = 1
configure:19711: $PKG_CONFIG --exists --print-errors "libuna >= 20120425"
Package libuna was not found in the pkg-config search path.
Perhaps you should add the directory containing `libuna.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libuna' found
configure:19714: $? = 1
configure:19727: result: no
No package 'libuna' found
configure:19764: checking libuna.h usability
configure:19764: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:124:20: fatal error: libuna.h: No such file or directory
compilation terminated.
configure:19764: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libuna.h>
configure:19764: result: no
configure:19764: checking libuna.h presence
configure:19764: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:91:20: fatal error: libuna.h: No such file or directory
compilation terminated.
configure:19764: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| /* end confdefs.h.  */
| #include <libuna.h>
configure:19764: result: no
configure:19764: checking for libuna.h
configure:19764: result: no
configure:24535: checking whether to use search for libcfile in includedir and libdir or in the specified DIR, or no if to use local version
configure:24542: result: auto-detect
configure:24563: checking for libcfile
configure:24570: $PKG_CONFIG --exists --print-errors "libcfile >= 20120526"
Package libcfile was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcfile.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcfile' found
configure:24573: $? = 1
configure:24586: $PKG_CONFIG --exists --print-errors "libcfile >= 20120526"
Package libcfile was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcfile.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcfile' found
configure:24589: $? = 1
configure:24602: result: no
No package 'libcfile' found
configure:24639: checking libcfile.h usability
configure:24639: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:125:22: fatal error: libcfile.h: No such file or directory
compilation terminated.
configure:24639: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcfile.h>
configure:24639: result: no
configure:24639: checking libcfile.h presence
configure:24639: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:92:22: fatal error: libcfile.h: No such file or directory
compilation terminated.
configure:24639: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| /* end confdefs.h.  */
| #include <libcfile.h>
configure:24639: result: no
configure:24639: checking for libcfile.h
configure:24639: result: no
configure:25750: checking for errno.h
configure:25750: result: yes
configure:25750: checking for sys/stat.h
configure:25750: result: yes
configure:25764: checking fcntl.h usability
configure:25764: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:25764: $? = 0
configure:25764: result: yes
configure:25764: checking fcntl.h presence
configure:25764: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:25764: $? = 0
configure:25764: result: yes
configure:25764: checking for fcntl.h
configure:25764: result: yes
configure:25764: checking for unistd.h
configure:25764: result: yes
configure:25778: checking for close
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25778: checking for fstat
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25778: checking for ftruncate
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25778: checking for lseek
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25778: checking for open
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25778: checking for read
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25778: checking for write
configure:25778: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25778: $? = 0
configure:25778: result: yes
configure:25847: checking for fclose
configure:25847: result: yes
configure:25847: checking for feof
configure:25847: result: yes
configure:25847: checking for fopen
configure:25847: result: yes
configure:25847: checking for fread
configure:25847: result: yes
configure:25847: checking for fseeko
configure:25847: result: yes
configure:25847: checking for fseeko64
configure:25847: result: yes
configure:25847: checking for ftello
configure:25847: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25847: $? = 0
configure:25847: result: yes
configure:25847: checking for ftello64
configure:25847: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25847: $? = 0
configure:25847: result: yes
configure:25847: checking for fwrite
configure:25847: result: yes
configure:25923: checking for stat
configure:25923: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:25923: $? = 0
configure:25923: result: yes
configure:25996: checking whether to use search for libcpath in includedir and libdir or in the specified DIR, or no if to use local version
configure:26003: result: auto-detect
configure:26024: checking for libcpath
configure:26031: $PKG_CONFIG --exists --print-errors "libcpath >= 20120701"
Package libcpath was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcpath.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcpath' found
configure:26034: $? = 1
configure:26047: $PKG_CONFIG --exists --print-errors "libcpath >= 20120701"
Package libcpath was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcpath.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcpath' found
configure:26050: $? = 1
configure:26063: result: no
No package 'libcpath' found
configure:26100: checking libcpath.h usability
configure:26100: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:147:22: fatal error: libcpath.h: No such file or directory
compilation terminated.
configure:26100: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcpath.h>
configure:26100: result: no
configure:26100: checking libcpath.h presence
configure:26100: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:114:22: fatal error: libcpath.h: No such file or directory
compilation terminated.
configure:26100: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| /* end confdefs.h.  */
| #include <libcpath.h>
configure:26100: result: no
configure:26100: checking for libcpath.h
configure:26100: result: no
configure:26781: checking for errno.h
configure:26781: result: yes
configure:26781: checking for sys/stat.h
configure:26781: result: yes
configure:26781: checking sys/syslimits.h usability
configure:26781: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:149:27: fatal error: sys/syslimits.h: No such file or directory
compilation terminated.
configure:26781: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <sys/syslimits.h>
configure:26781: result: no
configure:26781: checking sys/syslimits.h presence
configure:26781: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:116:27: fatal error: sys/syslimits.h: No such file or directory
compilation terminated.
configure:26781: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| /* end confdefs.h.  */
| #include <sys/syslimits.h>
configure:26781: result: no
configure:26781: checking for sys/syslimits.h
configure:26781: result: no
configure:26795: checking for chdir
configure:26795: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:26795: $? = 0
configure:26795: result: yes
configure:26795: checking for getcwd
configure:26795: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:26795: $? = 0
configure:26795: result: yes
configure:26823: checking for mkdir
configure:26823: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:26823: $? = 0
configure:26823: result: yes
configure:26834: checking how to use mkdir
configure:26858: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:26858: $? = 0
configure:26859: result: with additional mode argument
configure:26986: checking whether to use search for libbfio in includedir and libdir or in the specified DIR, or no if to use local version
configure:26993: result: auto-detect
configure:27014: checking for libbfio
configure:27021: $PKG_CONFIG --exists --print-errors "libbfio >= 20120426"
Package libbfio was not found in the pkg-config search path.
Perhaps you should add the directory containing `libbfio.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libbfio' found
configure:27024: $? = 1
configure:27037: $PKG_CONFIG --exists --print-errors "libbfio >= 20120426"
Package libbfio was not found in the pkg-config search path.
Perhaps you should add the directory containing `libbfio.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libbfio' found
configure:27040: $? = 1
configure:27053: result: no
No package 'libbfio' found
configure:27090: checking libbfio.h usability
configure:27090: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:155:21: fatal error: libbfio.h: No such file or directory
compilation terminated.
configure:27090: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libbfio.h>
configure:27090: result: no
configure:27090: checking libbfio.h presence
configure:27090: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:122:21: fatal error: libbfio.h: No such file or directory
compilation terminated.
configure:27090: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| /* end confdefs.h.  */
| #include <libbfio.h>
configure:27090: result: no
configure:27090: checking for libbfio.h
configure:27090: result: no
configure:28792: checking whether to use search for libfvalue in includedir and libdir or in the specified DIR, or no if to use local version
configure:28799: result: auto-detect
configure:28820: checking for libfvalue
configure:28827: $PKG_CONFIG --exists --print-errors "libfvalue >= 20120428"
Package libfvalue was not found in the pkg-config search path.
Perhaps you should add the directory containing `libfvalue.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libfvalue' found
configure:28830: $? = 1
configure:28843: $PKG_CONFIG --exists --print-errors "libfvalue >= 20120428"
Package libfvalue was not found in the pkg-config search path.
Perhaps you should add the directory containing `libfvalue.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libfvalue' found
configure:28846: $? = 1
configure:28859: result: no
No package 'libfvalue' found
configure:28896: checking libfvalue.h usability
configure:28896: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:156:23: fatal error: libfvalue.h: No such file or directory
compilation terminated.
configure:28896: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libfvalue.h>
configure:28896: result: no
configure:28896: checking libfvalue.h presence
configure:28896: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:123:23: fatal error: libfvalue.h: No such file or directory
compilation terminated.
configure:28896: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| /* end confdefs.h.  */
| #include <libfvalue.h>
configure:28896: result: no
configure:28896: checking for libfvalue.h
configure:28896: result: no
configure:31403: checking whether to use search for libmfcache in includedir and libdir or in the specified DIR, or no if to use local version
configure:31410: result: auto-detect
configure:31431: checking for libmfcache
configure:31438: $PKG_CONFIG --exists --print-errors "libmfcache >= 20120425"
Package libmfcache was not found in the pkg-config search path.
Perhaps you should add the directory containing `libmfcache.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libmfcache' found
configure:31441: $? = 1
configure:31454: $PKG_CONFIG --exists --print-errors "libmfcache >= 20120425"
Package libmfcache was not found in the pkg-config search path.
Perhaps you should add the directory containing `libmfcache.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libmfcache' found
configure:31457: $? = 1
configure:31470: result: no
No package 'libmfcache' found
configure:31507: checking libmfcache.h usability
configure:31507: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:157:24: fatal error: libmfcache.h: No such file or directory
compilation terminated.
configure:31507: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libmfcache.h>
configure:31507: result: no
configure:31507: checking libmfcache.h presence
configure:31507: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:124:24: fatal error: libmfcache.h: No such file or directory
compilation terminated.
configure:31507: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| /* end confdefs.h.  */
| #include <libmfcache.h>
configure:31507: result: no
configure:31507: checking for libmfcache.h
configure:31507: result: no
configure:31593: checking whether struct tm is in sys/time.h or time.h
configure:31613: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:31613: $? = 0
configure:31620: result: time.h
configure:31629: checking whether time.h and sys/time.h may both be included
configure:31649: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:31649: $? = 0
configure:31656: result: yes
configure:31667: checking for time
configure:31667: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:31667: $? = 0
configure:31667: result: yes
configure:31738: checking whether to use search for libmfdata in includedir and libdir or in the specified DIR, or no if to use local version
configure:31745: result: auto-detect
configure:31766: checking for libmfdata
configure:31773: $PKG_CONFIG --exists --print-errors "libmfdata >= 20120425"
Package libmfdata was not found in the pkg-config search path.
Perhaps you should add the directory containing `libmfdata.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libmfdata' found
configure:31776: $? = 1
configure:31789: $PKG_CONFIG --exists --print-errors "libmfdata >= 20120425"
Package libmfdata was not found in the pkg-config search path.
Perhaps you should add the directory containing `libmfdata.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libmfdata' found
configure:31792: $? = 1
configure:31805: result: no
No package 'libmfdata' found
configure:31842: checking libmfdata.h usability
configure:31842: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:160:23: fatal error: libmfdata.h: No such file or directory
compilation terminated.
configure:31842: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libmfdata.h>
configure:31842: result: no
configure:31842: checking libmfdata.h presence
configure:31842: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:127:23: fatal error: libmfdata.h: No such file or directory
compilation terminated.
configure:31842: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| /* end confdefs.h.  */
| #include <libmfdata.h>
configure:31842: result: no
configure:31842: checking for libmfdata.h
configure:31842: result: no
configure:33927: checking whether to use search for zlib in includedir and libdir or in the specified DIR, or no if not to use zlib
configure:33934: result: auto-detect
configure:33943: checking whether to use specify which alder32 implementation to use, options: 'auto-detect', 'zlib' or 'local'
configure:33950: result: auto-detect
configure:33971: checking for zlib
configure:33978: $PKG_CONFIG --exists --print-errors "zlib >= 1.2.5"
Package zlib was not found in the pkg-config search path.
Perhaps you should add the directory containing `zlib.pc'
to the PKG_CONFIG_PATH environment variable
No package 'zlib' found
configure:33981: $? = 1
configure:33994: $PKG_CONFIG --exists --print-errors "zlib >= 1.2.5"
Package zlib was not found in the pkg-config search path.
Perhaps you should add the directory containing `zlib.pc'
to the PKG_CONFIG_PATH environment variable
No package 'zlib' found
configure:33997: $? = 1
configure:34010: result: no
No package 'zlib' found
configure:34047: checking zlib.h usability
configure:34047: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:161:18: fatal error: zlib.h: No such file or directory
compilation terminated.
configure:34047: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <zlib.h>
configure:34047: result: no
configure:34047: checking zlib.h presence
configure:34047: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:128:18: fatal error: zlib.h: No such file or directory
compilation terminated.
configure:34047: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <zlib.h>
configure:34047: result: no
configure:34047: checking for zlib.h
configure:34047: result: no
configure:34343: checking whether to use search for bzip2 in includedir and libdir or in the specified DIR, or no if not to use bzip2
configure:34350: result: auto-detect
configure:34371: checking for bzip2
configure:34378: $PKG_CONFIG --exists --print-errors "bzip2 >= 1.0"
Package bzip2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `bzip2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'bzip2' found
configure:34381: $? = 1
configure:34394: $PKG_CONFIG --exists --print-errors "bzip2 >= 1.0"
Package bzip2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `bzip2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'bzip2' found
configure:34397: $? = 1
configure:34410: result: no
No package 'bzip2' found
configure:34447: checking bzlib.h usability
configure:34447: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:161:19: fatal error: bzlib.h: No such file or directory
compilation terminated.
configure:34447: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <bzlib.h>
configure:34447: result: no
configure:34447: checking bzlib.h presence
configure:34447: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:128:19: fatal error: bzlib.h: No such file or directory
compilation terminated.
configure:34447: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <bzlib.h>
configure:34447: result: no
configure:34447: checking for bzlib.h
configure:34447: result: no
configure:34654: checking whether to use search for libhmac in includedir and libdir or in the specified DIR, or no if to use local version
configure:34661: result: auto-detect
configure:34682: checking for libhmac
configure:34689: $PKG_CONFIG --exists --print-errors "libhmac >= 20120425"
Package libhmac was not found in the pkg-config search path.
Perhaps you should add the directory containing `libhmac.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libhmac' found
configure:34692: $? = 1
configure:34705: $PKG_CONFIG --exists --print-errors "libhmac >= 20120425"
Package libhmac was not found in the pkg-config search path.
Perhaps you should add the directory containing `libhmac.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libhmac' found
configure:34708: $? = 1
configure:34721: result: no
No package 'libhmac' found
configure:34758: checking libhmac.h usability
configure:34758: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:161:21: fatal error: libhmac.h: No such file or directory
compilation terminated.
configure:34758: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libhmac.h>
configure:34758: result: no
configure:34758: checking libhmac.h presence
configure:34758: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:128:21: fatal error: libhmac.h: No such file or directory
compilation terminated.
configure:34758: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <libhmac.h>
configure:34758: result: no
configure:34758: checking for libhmac.h
configure:34758: result: no
configure:35560: checking whether to use search for openssl in includedir and libdir or in the specified DIR, or no if not to use openssl
configure:35567: result: auto-detect
configure:35588: checking for openssl
configure:35595: $PKG_CONFIG --exists --print-errors "openssl >= 1.0"
Package openssl was not found in the pkg-config search path.
Perhaps you should add the directory containing `openssl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'openssl' found
configure:35598: $? = 1
configure:35611: $PKG_CONFIG --exists --print-errors "openssl >= 1.0"
Package openssl was not found in the pkg-config search path.
Perhaps you should add the directory containing `openssl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'openssl' found
configure:35614: $? = 1
configure:35627: result: no
No package 'openssl' found
configure:35667: checking openssl/opensslv.h usability
configure:35667: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:161:30: fatal error: openssl/opensslv.h: No such file or directory
compilation terminated.
configure:35667: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <openssl/opensslv.h>
configure:35667: result: no
configure:35667: checking openssl/opensslv.h presence
configure:35667: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:128:30: fatal error: openssl/opensslv.h: No such file or directory
compilation terminated.
configure:35667: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <openssl/opensslv.h>
configure:35667: result: no
configure:35667: checking for openssl/opensslv.h
configure:35667: result: no
configure:35680: checking openssl/evp.h usability
configure:35680: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:161:25: fatal error: openssl/evp.h: No such file or directory
compilation terminated.
configure:35680: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <openssl/evp.h>
configure:35680: result: no
configure:35680: checking openssl/evp.h presence
configure:35680: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:128:25: fatal error: openssl/evp.h: No such file or directory
compilation terminated.
configure:35680: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| /* end confdefs.h.  */
| #include <openssl/evp.h>
configure:35680: result: no
configure:35680: checking for openssl/evp.h
configure:35680: result: no
configure:37197: checking whether to use search for libcaes in includedir and libdir or in the specified DIR, or no if to use local version
configure:37204: result: auto-detect
configure:37225: checking for libcaes
configure:37232: $PKG_CONFIG --exists --print-errors "libcaes >= 20120425"
Package libcaes was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcaes.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcaes' found
configure:37235: $? = 1
configure:37248: $PKG_CONFIG --exists --print-errors "libcaes >= 20120425"
Package libcaes was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcaes.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcaes' found
configure:37251: $? = 1
configure:37264: result: no
No package 'libcaes' found
configure:37301: checking libcaes.h usability
configure:37301: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:162:21: fatal error: libcaes.h: No such file or directory
compilation terminated.
configure:37301: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcaes.h>
configure:37301: result: no
configure:37301: checking libcaes.h presence
configure:37301: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:129:21: fatal error: libcaes.h: No such file or directory
compilation terminated.
configure:37301: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| /* end confdefs.h.  */
| #include <libcaes.h>
configure:37301: result: no
configure:37301: checking for libcaes.h
configure:37301: result: no
configure:37431: checking whether to use search for openssl in includedir and libdir or in the specified DIR, or no if not to use openssl
configure:37438: result: auto-detect
configure:37459: checking for openssl
configure:37466: $PKG_CONFIG --exists --print-errors "openssl >= 1.0"
Package openssl was not found in the pkg-config search path.
Perhaps you should add the directory containing `openssl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'openssl' found
configure:37469: $? = 1
configure:37482: $PKG_CONFIG --exists --print-errors "openssl >= 1.0"
Package openssl was not found in the pkg-config search path.
Perhaps you should add the directory containing `openssl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'openssl' found
configure:37485: $? = 1
configure:37498: result: no
No package 'openssl' found
configure:37538: checking for openssl/opensslv.h
configure:37538: result: no
configure:37551: checking for openssl/evp.h
configure:37551: result: no
configure:38194: checking whether struct tm is in sys/time.h or time.h
configure:38221: result: time.h
configure:38230: checking whether time.h and sys/time.h may both be included
configure:38257: result: yes
configure:38269: checking for localtime
configure:38269: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38269: $? = 0
configure:38269: result: yes
configure:38269: checking for localtime_r
configure:38269: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38269: $? = 0
configure:38269: result: yes
configure:38269: checking for mktime
configure:38269: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38269: $? = 0
configure:38269: result: yes
configure:38297: checking for bindtextdomain
configure:38297: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38297: $? = 0
configure:38297: result: yes
configure:38315: checking whether to use search for libcsystem in includedir and libdir or in the specified DIR, or no if to use local version
configure:38322: result: auto-detect
configure:38343: checking for libcsystem
configure:38350: $PKG_CONFIG --exists --print-errors "libcsystem >= 20120425"
Package libcsystem was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcsystem.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcsystem' found
configure:38353: $? = 1
configure:38366: $PKG_CONFIG --exists --print-errors "libcsystem >= 20120425"
Package libcsystem was not found in the pkg-config search path.
Perhaps you should add the directory containing `libcsystem.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libcsystem' found
configure:38369: $? = 1
configure:38382: result: no
No package 'libcsystem' found
configure:38419: checking libcsystem.h usability
configure:38419: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:168:24: fatal error: libcsystem.h: No such file or directory
compilation terminated.
configure:38419: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libcsystem.h>
configure:38419: result: no
configure:38419: checking libcsystem.h presence
configure:38419: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:135:24: fatal error: libcsystem.h: No such file or directory
compilation terminated.
configure:38419: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| /* end confdefs.h.  */
| #include <libcsystem.h>
configure:38419: result: no
configure:38419: checking for libcsystem.h
configure:38419: result: no
configure:38505: checking whether struct tm is in sys/time.h or time.h
configure:38532: result: time.h
configure:38543: checking for errno.h
configure:38543: result: yes
configure:38557: checking for fcntl.h
configure:38557: result: yes
configure:38557: checking for unistd.h
configure:38557: result: yes
configure:38557: checking for sys/stat.h
configure:38557: result: yes
configure:38568: checking whether time.h and sys/time.h may both be included
configure:38595: result: yes
configure:38606: checking glob.h usability
configure:38606: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:38606: $? = 0
configure:38606: result: yes
configure:38606: checking glob.h presence
configure:38606: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:38606: $? = 0
configure:38606: result: yes
configure:38606: checking for glob.h
configure:38606: result: yes
configure:38636: checking signal.h usability
configure:38636: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:38636: $? = 0
configure:38636: result: yes
configure:38636: checking signal.h presence
configure:38636: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:38636: $? = 0
configure:38636: result: yes
configure:38636: checking for signal.h
configure:38636: result: yes
configure:38636: checking sys/signal.h usability
configure:38636: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:38636: $? = 0
configure:38636: result: yes
configure:38636: checking sys/signal.h presence
configure:38636: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:38636: $? = 0
configure:38636: result: yes
configure:38636: checking for sys/signal.h
configure:38636: result: yes
configure:38650: checking for close
configure:38650: result: yes
configure:38650: checking for fstat
configure:38650: result: yes
configure:38650: checking for ftruncate
configure:38650: result: yes
configure:38650: checking for lseek
configure:38650: result: yes
configure:38650: checking for open
configure:38650: result: yes
configure:38650: checking for read
configure:38650: result: yes
configure:38650: checking for stat
configure:38650: result: yes
configure:38650: checking for write
configure:38650: result: yes
configure:38727: checking for localtime
configure:38727: result: yes
configure:38727: checking for localtime_r
configure:38727: result: yes
configure:38727: checking for mktime
configure:38727: result: yes
configure:38755: checking for ctime_r
configure:38755: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38755: $? = 0
configure:38755: result: yes
configure:38766: checking how to use ctime_r
configure:38787: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
conftest.c: In function 'main':
conftest.c:159:1: error: too many arguments to function 'ctime_r'
/usr/include/time.h:270:14: note: declared here
configure:38787: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| /* end confdefs.h.  */
| #include <time.h>
| int
| main ()
| {
| ctime_r( NULL, NULL, 0 )
|   ;
|   return 0;
| }
configure:38809: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38809: $? = 0
configure:38810: result: with two arguments
configure:38902: checking for gmtime
configure:38902: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38902: $? = 0
configure:38902: result: yes
configure:38902: checking for gmtime_r
configure:38902: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38902: $? = 0
configure:38902: result: yes
configure:38902: checking for time
configure:38902: result: yes
configure:38930: checking for getopt
configure:38930: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38930: $? = 0
configure:38930: result: yes
configure:38942: checking for setvbuf
configure:38942: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38942: $? = 0
configure:38942: result: yes
configure:38955: checking for bindtextdomain
configure:38955: result: yes
configure:38955: checking for textdomain
configure:38955: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:38955: $? = 0
configure:38955: result: yes
configure:39020: checking whether to use search for libuuid in includedir and libdir or in the specified DIR, or no if not to use libuuid
configure:39027: result: auto-detect
configure:39056: checking for uuid
configure:39063: $PKG_CONFIG --exists --print-errors "uuid >= 2.20"
Package uuid was not found in the pkg-config search path.
Perhaps you should add the directory containing `uuid.pc'
to the PKG_CONFIG_PATH environment variable
No package 'uuid' found
configure:39066: $? = 1
configure:39079: $PKG_CONFIG --exists --print-errors "uuid >= 2.20"
Package uuid was not found in the pkg-config search path.
Perhaps you should add the directory containing `uuid.pc'
to the PKG_CONFIG_PATH environment variable
No package 'uuid' found
configure:39082: $? = 1
configure:39095: result: no
No package 'uuid' found
configure:39132: checking uuid/uuid.h usability
configure:39132: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:197:23: fatal error: uuid/uuid.h: No such file or directory
compilation terminated.
configure:39132: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <uuid/uuid.h>
configure:39132: result: no
configure:39132: checking uuid/uuid.h presence
configure:39132: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:164:23: fatal error: uuid/uuid.h: No such file or directory
compilation terminated.
configure:39132: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| /* end confdefs.h.  */
| #include <uuid/uuid.h>
configure:39132: result: no
configure:39132: checking for uuid/uuid.h
configure:39132: result: no
configure:39373: checking for flex
configure:39403: result: no
configure:39373: checking for lex
configure:39403: result: no
configure:39534: checking whether to use search for libodraw in includedir and libdir or in the specified DIR, or no if to use local version
configure:39541: result: auto-detect
configure:39562: checking for libodraw
configure:39569: $PKG_CONFIG --exists --print-errors "libodraw >= 20120630"
Package libodraw was not found in the pkg-config search path.
Perhaps you should add the directory containing `libodraw.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libodraw' found
configure:39572: $? = 1
configure:39585: $PKG_CONFIG --exists --print-errors "libodraw >= 20120630"
Package libodraw was not found in the pkg-config search path.
Perhaps you should add the directory containing `libodraw.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libodraw' found
configure:39588: $? = 1
configure:39601: result: no
No package 'libodraw' found
configure:39638: checking libodraw.h usability
configure:39638: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:197:22: fatal error: libodraw.h: No such file or directory
compilation terminated.
configure:39638: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libodraw.h>
configure:39638: result: no
configure:39638: checking libodraw.h presence
configure:39638: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:164:22: fatal error: libodraw.h: No such file or directory
compilation terminated.
configure:39638: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| /* end confdefs.h.  */
| #include <libodraw.h>
configure:39638: result: no
configure:39638: checking for libodraw.h
configure:39638: result: no
configure:40580: checking for bison
configure:40610: result: no
configure:40580: checking for byacc
configure:40610: result: no
configure:40675: checking whether to use search for libmsdev in includedir and libdir or in the specified DIR, or no if to use local version
configure:40682: result: auto-detect
configure:40703: checking for libsmdev
configure:40710: $PKG_CONFIG --exists --print-errors "libsmdev >= 20120630"
Package libsmdev was not found in the pkg-config search path.
Perhaps you should add the directory containing `libsmdev.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libsmdev' found
configure:40713: $? = 1
configure:40726: $PKG_CONFIG --exists --print-errors "libsmdev >= 20120630"
Package libsmdev was not found in the pkg-config search path.
Perhaps you should add the directory containing `libsmdev.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libsmdev' found
configure:40729: $? = 1
configure:40742: result: no
No package 'libsmdev' found
configure:40779: checking libsmdev.h usability
configure:40779: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:198:22: fatal error: libsmdev.h: No such file or directory
compilation terminated.
configure:40779: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libsmdev.h>
configure:40779: result: no
configure:40779: checking libsmdev.h presence
configure:40779: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:165:22: fatal error: libsmdev.h: No such file or directory
compilation terminated.
configure:40779: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| /* end confdefs.h.  */
| #include <libsmdev.h>
configure:40779: result: no
configure:40779: checking for libsmdev.h
configure:40779: result: no
configure:41929: checking for errno.h
configure:41929: result: yes
configure:41929: checking for fcntl.h
configure:41929: result: yes
configure:41929: checking for sys/stat.h
configure:41929: result: yes
configure:41929: checking for unistd.h
configure:41929: result: yes
configure:41944: checking cygwin/fs.h usability
configure:41944: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:202:23: fatal error: cygwin/fs.h: No such file or directory
compilation terminated.
configure:41944: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <cygwin/fs.h>
configure:41944: result: no
configure:41944: checking cygwin/fs.h presence
configure:41944: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:169:23: fatal error: cygwin/fs.h: No such file or directory
compilation terminated.
configure:41944: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| /* end confdefs.h.  */
| #include <cygwin/fs.h>
configure:41944: result: no
configure:41944: checking for cygwin/fs.h
configure:41944: result: no
configure:41944: checking linux/fs.h usability
configure:41944: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41944: $? = 0
configure:41944: result: yes
configure:41944: checking linux/fs.h presence
configure:41944: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41944: $? = 0
configure:41944: result: yes
configure:41944: checking for linux/fs.h
configure:41944: result: yes
configure:41944: checking sys/disk.h usability
configure:41944: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:203:22: fatal error: sys/disk.h: No such file or directory
compilation terminated.
configure:41944: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <sys/disk.h>
configure:41944: result: no
configure:41944: checking sys/disk.h presence
configure:41944: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:170:22: fatal error: sys/disk.h: No such file or directory
compilation terminated.
configure:41944: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| /* end confdefs.h.  */
| #include <sys/disk.h>
configure:41944: result: no
configure:41944: checking for sys/disk.h
configure:41944: result: no
configure:41944: checking sys/disklabel.h usability
configure:41944: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:203:27: fatal error: sys/disklabel.h: No such file or directory
compilation terminated.
configure:41944: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <sys/disklabel.h>
configure:41944: result: no
configure:41944: checking sys/disklabel.h presence
configure:41944: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:170:27: fatal error: sys/disklabel.h: No such file or directory
compilation terminated.
configure:41944: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| /* end confdefs.h.  */
| #include <sys/disklabel.h>
configure:41944: result: no
configure:41944: checking for sys/disklabel.h
configure:41944: result: no
configure:41944: checking sys/ioctl.h usability
configure:41944: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41944: $? = 0
configure:41944: result: yes
configure:41944: checking sys/ioctl.h presence
configure:41944: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41944: $? = 0
configure:41944: result: yes
configure:41944: checking for sys/ioctl.h
configure:41944: result: yes
configure:41961: checking cygwin/hdreg.h usability
configure:41961: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:204:26: fatal error: cygwin/hdreg.h: No such file or directory
compilation terminated.
configure:41961: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <cygwin/hdreg.h>
configure:41961: result: no
configure:41961: checking cygwin/hdreg.h presence
configure:41961: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:171:26: fatal error: cygwin/hdreg.h: No such file or directory
compilation terminated.
configure:41961: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| /* end confdefs.h.  */
| #include <cygwin/hdreg.h>
configure:41961: result: no
configure:41961: checking for cygwin/hdreg.h
configure:41961: result: no
configure:41961: checking linux/hdreg.h usability
configure:41961: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41961: $? = 0
configure:41961: result: yes
configure:41961: checking linux/hdreg.h presence
configure:41961: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41961: $? = 0
configure:41961: result: yes
configure:41961: checking for linux/hdreg.h
configure:41961: result: yes
configure:41978: checking scsi/scsi.h usability
configure:41978: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41978: $? = 0
configure:41978: result: yes
configure:41978: checking scsi/scsi.h presence
configure:41978: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41978: $? = 0
configure:41978: result: yes
configure:41978: checking for scsi/scsi.h
configure:41978: result: yes
configure:41978: checking scsi/scsi_ioctl.h usability
configure:41978: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41978: $? = 0
configure:41978: result: yes
configure:41978: checking scsi/scsi_ioctl.h presence
configure:41978: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41978: $? = 0
configure:41978: result: yes
configure:41978: checking for scsi/scsi_ioctl.h
configure:41978: result: yes
configure:41978: checking scsi/sg.h usability
configure:41978: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41978: $? = 0
configure:41978: result: yes
configure:41978: checking scsi/sg.h presence
configure:41978: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41978: $? = 0
configure:41978: result: yes
configure:41978: checking for scsi/sg.h
configure:41978: result: yes
configure:41994: checking linux/cdrom.h usability
configure:41994: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:41994: $? = 0
configure:41994: result: yes
configure:41994: checking linux/cdrom.h presence
configure:41994: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:41994: $? = 0
configure:41994: result: yes
configure:41994: checking for linux/cdrom.h
configure:41994: result: yes
configure:42011: checking linux/usbdevice_fs.h usability
configure:42011: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:42011: $? = 0
configure:42011: result: yes
configure:42011: checking linux/usbdevice_fs.h presence
configure:42011: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:42011: $? = 0
configure:42011: result: yes
configure:42011: checking for linux/usbdevice_fs.h
configure:42011: result: yes
configure:42011: checking linux/usb/ch9.h usability
configure:42011: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
configure:42011: $? = 0
configure:42011: result: yes
configure:42011: checking linux/usb/ch9.h presence
configure:42011: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:42011: $? = 0
configure:42011: result: yes
configure:42011: checking for linux/usb/ch9.h
configure:42011: result: yes
configure:42027: checking for close
configure:42027: result: yes
configure:42027: checking for fstat
configure:42027: result: yes
configure:42027: checking for ftruncate
configure:42027: result: yes
configure:42027: checking for lseek
configure:42027: result: yes
configure:42027: checking for open
configure:42027: result: yes
configure:42027: checking for read
configure:42027: result: yes
configure:42027: checking for stat
configure:42027: result: yes
configure:42027: checking for write
configure:42027: result: yes
configure:42103: checking for posix_fadvise
configure:42103: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:42103: $? = 0
configure:42103: result: yes
configure:42114: checking whether posix_fadvise can be linked
configure:42140: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Wall -Werror -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:42140: $? = 0
configure:42157: result: yes
configure:42170: checking whether strerror_r is declared
configure:42170: result: yes
configure:42183: checking for strerror_r
configure:42183: result: yes
configure:42192: checking whether strerror_r returns char *
configure:42254: result: no
configure:42392: checking whether to use search for libmsraw in includedir and libdir or in the specified DIR, or no if to use local version
configure:42399: result: auto-detect
configure:42420: checking for libsmraw
configure:42427: $PKG_CONFIG --exists --print-errors "libsmraw >= 20120630"
Package libsmraw was not found in the pkg-config search path.
Perhaps you should add the directory containing `libsmraw.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libsmraw' found
configure:42430: $? = 1
configure:42443: $PKG_CONFIG --exists --print-errors "libsmraw >= 20120630"
Package libsmraw was not found in the pkg-config search path.
Perhaps you should add the directory containing `libsmraw.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libsmraw' found
configure:42446: $? = 1
configure:42459: result: no
No package 'libsmraw' found
configure:42496: checking libsmraw.h usability
configure:42496: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:224:22: fatal error: libsmraw.h: No such file or directory
compilation terminated.
configure:42496: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <libsmraw.h>
configure:42496: result: no
configure:42496: checking libsmraw.h presence
configure:42496: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:191:22: fatal error: libsmraw.h: No such file or directory
compilation terminated.
configure:42496: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| /* end confdefs.h.  */
| #include <libsmraw.h>
configure:42496: result: no
configure:42496: checking for libsmraw.h
configure:42496: result: no
configure:43375: checking whether to use search for libfuse in includedir and libdir or in the specified DIR, or no if not to use libfuse
configure:43382: result: auto-detect
configure:43403: checking for fuse
configure:43410: $PKG_CONFIG --exists --print-errors "fuse >= 2.6"
Package fuse was not found in the pkg-config search path.
Perhaps you should add the directory containing `fuse.pc'
to the PKG_CONFIG_PATH environment variable
No package 'fuse' found
configure:43413: $? = 1
configure:43426: $PKG_CONFIG --exists --print-errors "fuse >= 2.6"
Package fuse was not found in the pkg-config search path.
Perhaps you should add the directory containing `fuse.pc'
to the PKG_CONFIG_PATH environment variable
No package 'fuse' found
configure:43429: $? = 1
configure:43442: result: no
No package 'fuse' found
configure:43479: checking fuse.h usability
configure:43479: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 conftest.c >&5
conftest.c:225:18: fatal error: fuse.h: No such file or directory
compilation terminated.
configure:43479: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <fuse.h>
configure:43479: result: no
configure:43479: checking fuse.h presence
configure:43479: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:192:18: fatal error: fuse.h: No such file or directory
compilation terminated.
configure:43479: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <fuse.h>
configure:43479: result: no
configure:43479: checking for fuse.h
configure:43479: result: no
configure:43497: checking fuse.h usability
configure:43497: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 conftest.c >&5
conftest.c:225:18: fatal error: fuse.h: No such file or directory
compilation terminated.
configure:43497: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <fuse.h>
configure:43497: result: no
configure:43497: checking fuse.h presence
configure:43497: gcc -E -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 conftest.c
conftest.c:192:18: fatal error: fuse.h: No such file or directory
compilation terminated.
configure:43497: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <fuse.h>
configure:43497: result: no
configure:43497: checking for fuse.h
configure:43497: result: no
configure:43694: checking osxfuse/fuse.h usability
configure:43694: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 conftest.c >&5
conftest.c:225:26: fatal error: osxfuse/fuse.h: No such file or directory
compilation terminated.
configure:43694: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <osxfuse/fuse.h>
configure:43694: result: no
configure:43694: checking osxfuse/fuse.h presence
configure:43694: gcc -E -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 conftest.c
conftest.c:192:26: fatal error: osxfuse/fuse.h: No such file or directory
compilation terminated.
configure:43694: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <osxfuse/fuse.h>
configure:43694: result: no
configure:43694: checking for osxfuse/fuse.h
configure:43694: result: no
configure:43710: checking osxfuse/fuse.h usability
configure:43710: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 conftest.c >&5
conftest.c:225:26: fatal error: osxfuse/fuse.h: No such file or directory
compilation terminated.
configure:43710: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <osxfuse/fuse.h>
configure:43710: result: no
configure:43710: checking osxfuse/fuse.h presence
configure:43710: gcc -E -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 conftest.c
conftest.c:192:26: fatal error: osxfuse/fuse.h: No such file or directory
compilation terminated.
configure:43710: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "libewf"
| #define PACKAGE_TARNAME "libewf"
| #define PACKAGE_VERSION "20120809"
| #define PACKAGE_STRING "libewf 20120809"
| #define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
| #define PACKAGE_URL ""
| #define PACKAGE "libewf"
| #define VERSION "20120809"
| #define _FILE_OFFSET_BITS 64
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
| #define LT_OBJDIR ".libs/"
| #define ENABLE_NLS 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define SIZEOF_OFF_T 8
| #define SIZEOF_SIZE_T 4
| #define HAVE_LIBINTL_H 1
| #define HAVE_LIMITS_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FGETS 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FWRITE 1
| #define HAVE_VFPRINTF 1
| #define HAVE_FREE 1
| #define HAVE_MALLOC 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMSET 1
| #define HAVE_REALLOC 1
| #define HAVE_PRINTF_JD 1
| #define HAVE_PRINTF_ZD 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_WCHAR_H 1
| #define HAVE_WCTYPE_H 1
| #define HAVE_FGETS 1
| #define HAVE_MEMCHR 1
| #define HAVE_MEMCMP 1
| #define HAVE_MEMCPY 1
| #define HAVE_MEMRCHR 1
| #define HAVE_SNPRINTF 1
| #define HAVE_SSCANF 1
| #define HAVE_STRCASECMP 1
| #define HAVE_STRCHR 1
| #define HAVE_STRLEN 1
| #define HAVE_STRNCASECMP 1
| #define HAVE_STRNCMP 1
| #define HAVE_STRNCPY 1
| #define HAVE_STRRCHR 1
| #define HAVE_STRSTR 1
| #define HAVE_VSNPRINTF 1
| #define HAVE_DECL_MEMRCHR 0
| #define HAVE_LOCAL_LIBCSTRING 1
| #define HAVE_STDARG_H 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBCERROR 1
| #define HAVE_LANGINFO_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_GETENV 1
| #define HAVE_LOCALECONV 1
| #define HAVE_SETLOCALE 1
| #define HAVE_NL_LANGINFO 1
| #define HAVE_LANGINFO_CODESET 1
| #define HAVE_LOCAL_LIBCLOCALE 1
| #define HAVE_STDARG_H 1
| #define HAVE_ERRNO_H 1
| #define HAVE_LOCAL_LIBCNOTIFY 1
| #define HAVE_LOCAL_LIBCSPLIT 1
| #define HAVE_LOCAL_LIBUNA 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_WRITE 1
| #define HAVE_FCLOSE 1
| #define HAVE_FEOF 1
| #define HAVE_FOPEN 1
| #define HAVE_FREAD 1
| #define HAVE_FSEEKO 1
| #define HAVE_FSEEKO64 1
| #define HAVE_FTELLO 1
| #define HAVE_FTELLO64 1
| #define HAVE_FWRITE 1
| #define HAVE_STAT 1
| #define HAVE_LOCAL_LIBCFILE 1
| #define HAVE_ERRNO_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_CHDIR 1
| #define HAVE_GETCWD 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR 1
| #define HAVE_MKDIR_MODE 1
| #define HAVE_LOCAL_LIBCPATH 1
| #define HAVE_LOCAL_LIBBFIO 1
| #define HAVE_LOCAL_LIBFVALUE 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_TIME 1
| #define HAVE_LOCAL_LIBMFCACHE 1
| #define HAVE_LOCAL_LIBMFDATA 1
| #define HAVE_LOCAL_LIBHMAC 1
| #define HAVE_LOCAL_LIBCAES 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_SYS_STAT_H 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_GLOB_H 1
| #define HAVE_SIGNAL_H 1
| #define HAVE_SYS_SIGNAL_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_LOCALTIME 1
| #define HAVE_LOCALTIME_R 1
| #define HAVE_MKTIME 1
| #define HAVE_CTIME_R 1
| #define HAVE_CTIME_R 1
| #define HAVE_GMTIME 1
| #define HAVE_GMTIME_R 1
| #define HAVE_TIME 1
| #define HAVE_GETOPT 1
| #define HAVE_SETVBUF 1
| #define HAVE_BINDTEXTDOMAIN 1
| #define HAVE_TEXTDOMAIN 1
| #define HAVE_LOCAL_LIBCSYSTEM 1
| #define HAVE_LOCAL_LIBODRAW 1
| #define HAVE_ERRNO_H 1
| #define HAVE_FCNTL_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LINUX_FS_H 1
| #define HAVE_SYS_IOCTL_H 1
| #define HAVE_LINUX_HDREG_H 1
| #define HAVE_SCSI_SCSI_H 1
| #define HAVE_SCSI_SCSI_IOCTL_H 1
| #define HAVE_SCSI_SG_H 1
| #define HAVE_LINUX_CDROM_H 1
| #define HAVE_LINUX_USBDEVICE_FS_H 1
| #define HAVE_LINUX_USB_CH9_H 1
| #define HAVE_CLOSE 1
| #define HAVE_FSTAT 1
| #define HAVE_FTRUNCATE 1
| #define HAVE_LSEEK 1
| #define HAVE_OPEN 1
| #define HAVE_READ 1
| #define HAVE_STAT 1
| #define HAVE_WRITE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_POSIX_FADVISE 1
| #define HAVE_DECL_STRERROR_R 1
| #define HAVE_STRERROR_R 1
| #define HAVE_LOCAL_LIBSMDEV 1
| #define HAVE_LOCAL_LIBSMRAW 1
| /* end confdefs.h.  */
| #include <osxfuse/fuse.h>
configure:43710: result: no
configure:43710: checking for osxfuse/fuse.h
configure:43710: result: no
configure:43963: checking sys/resource.h usability
configure:43963: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 conftest.c >&5
configure:43963: $? = 0
configure:43963: result: yes
configure:43963: checking sys/resource.h presence
configure:43963: gcc -E -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 conftest.c
configure:43963: $? = 0
configure:43963: result: yes
configure:43963: checking for sys/resource.h
configure:43963: result: yes
configure:43963: checking sys/utsname.h usability
configure:43963: gcc -c -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 conftest.c >&5
configure:43963: $? = 0
configure:43963: result: yes
configure:43963: checking sys/utsname.h presence
configure:43963: gcc -E -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 conftest.c
configure:43963: $? = 0
configure:43963: result: yes
configure:43963: checking for sys/utsname.h
configure:43963: result: yes
configure:43976: checking for getegid
configure:43976: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:43976: $? = 0
configure:43976: result: yes
configure:43976: checking for geteuid
configure:43976: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:43976: $? = 0
configure:43976: result: yes
configure:43976: checking for getrlimit
configure:43976: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:43976: $? = 0
configure:43976: result: yes
configure:43976: checking for getuid
configure:43976: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:43976: $? = 0
configure:43976: result: yes
configure:43976: checking for uname
configure:43976: gcc -o conftest -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64 -Wl,-Bsymbolic-functions -Wl,-z,relro conftest.c  >&5
configure:43976: $? = 0
configure:43976: result: yes
configure:43994: checking whether to enable build static executables (binaries)
configure:44001: result: no
configure:44019: checking whether to enable use libewf's low level read and write functions in the ewftools
configure:44026: result: no
configure:44044: checking whether to enable enable verbose output
configure:44051: result: no
configure:44069: checking whether to enable enable debug output
configure:44076: result: no
configure:44094: checking whether to enable build Python bindings
configure:44101: result: yes
configure:44136: checking for a Python interpreter with version >= 2.5
configure:44153: python -c import sys # split strings by '.' and convert to numeric. Append some zeros # because we need at least 4 digits for the hex conversion. # map returns an iterator in Python 3.0 and a list in 2.x minver = list(map(int, '2.5'.split('.'))) + [0, 0, 0] minverhex = 0 # xrange is not present in Python 3.0 and range returns an iterator for i in list(range(0, 4)): minverhex = (minverhex << 8) + minver[i] sys.exit(sys.hexversion < minverhex)
configure:44156: $? = 0
configure:44162: result: python
configure:44170: checking for python
configure:44188: found /usr/bin/python
configure:44200: result: /usr/bin/python
configure:44218: checking for python version
configure:44225: result: 2.7
configure:44237: checking for python platform
configure:44244: result: linux2
configure:44251: checking for python script directory
configure:44280: result: ${prefix}/lib/python2.7/dist-packages
configure:44289: checking for python extension module directory
configure:44318: result: ${exec_prefix}/lib/python2.7/dist-packages
configure:44333: checking for Python include path
configure:44337: result: /usr/include/python2.7
configure:44344: error: Missing Python include file

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_bzip2=no
ac_cv_c_compiler_gnu=yes
ac_cv_c_const=yes
ac_cv_c_volatile=yes
ac_cv_cv_ctime_r_posix=yes
ac_cv_cv_ctime_r_size=no
ac_cv_cv_have_printf_jd=yes
ac_cv_cv_have_printf_zd=yes
ac_cv_cv_langinfo_codeset=yes
ac_cv_cv_mkdir_mode=yes
ac_cv_enable_debug_output=no
ac_cv_enable_low_level_functions=no
ac_cv_enable_python=yes
ac_cv_enable_static_executables=no
ac_cv_enable_verbose_output=no
ac_cv_enable_wide_character_type=no
ac_cv_enable_winapi=no
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=set
ac_cv_env_CFLAGS_value='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security'
ac_cv_env_CPPFLAGS_set=set
ac_cv_env_CPPFLAGS_value=-D_FORTIFY_SOURCE=2
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=set
ac_cv_env_LDFLAGS_value='-Wl,-Bsymbolic-functions -Wl,-z,relro'
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_PKG_CONFIG_LIBDIR_set=
ac_cv_env_PKG_CONFIG_LIBDIR_value=
ac_cv_env_PKG_CONFIG_PATH_set=
ac_cv_env_PKG_CONFIG_PATH_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_YACC_set=
ac_cv_env_YACC_value=
ac_cv_env_YFLAGS_set=
ac_cv_env_YFLAGS_value=
ac_cv_env_build_alias_set=set
ac_cv_env_build_alias_value=i686-linux-gnu
ac_cv_env_bzip2_CFLAGS_set=
ac_cv_env_bzip2_CFLAGS_value=
ac_cv_env_bzip2_LIBS_set=
ac_cv_env_bzip2_LIBS_value=
ac_cv_env_fuse_CFLAGS_set=
ac_cv_env_fuse_CFLAGS_value=
ac_cv_env_fuse_LIBS_set=
ac_cv_env_fuse_LIBS_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_libbfio_CFLAGS_set=
ac_cv_env_libbfio_CFLAGS_value=
ac_cv_env_libbfio_LIBS_set=
ac_cv_env_libbfio_LIBS_value=
ac_cv_env_libcaes_CFLAGS_set=
ac_cv_env_libcaes_CFLAGS_value=
ac_cv_env_libcaes_LIBS_set=
ac_cv_env_libcaes_LIBS_value=
ac_cv_env_libcerror_CFLAGS_set=
ac_cv_env_libcerror_CFLAGS_value=
ac_cv_env_libcerror_LIBS_set=
ac_cv_env_libcerror_LIBS_value=
ac_cv_env_libcfile_CFLAGS_set=
ac_cv_env_libcfile_CFLAGS_value=
ac_cv_env_libcfile_LIBS_set=
ac_cv_env_libcfile_LIBS_value=
ac_cv_env_libclocale_CFLAGS_set=
ac_cv_env_libclocale_CFLAGS_value=
ac_cv_env_libclocale_LIBS_set=
ac_cv_env_libclocale_LIBS_value=
ac_cv_env_libcnotify_CFLAGS_set=
ac_cv_env_libcnotify_CFLAGS_value=
ac_cv_env_libcnotify_LIBS_set=
ac_cv_env_libcnotify_LIBS_value=
ac_cv_env_libcpath_CFLAGS_set=
ac_cv_env_libcpath_CFLAGS_value=
ac_cv_env_libcpath_LIBS_set=
ac_cv_env_libcpath_LIBS_value=
ac_cv_env_libcsplit_CFLAGS_set=
ac_cv_env_libcsplit_CFLAGS_value=
ac_cv_env_libcsplit_LIBS_set=
ac_cv_env_libcsplit_LIBS_value=
ac_cv_env_libcstring_CFLAGS_set=
ac_cv_env_libcstring_CFLAGS_value=
ac_cv_env_libcstring_LIBS_set=
ac_cv_env_libcstring_LIBS_value=
ac_cv_env_libcsystem_CFLAGS_set=
ac_cv_env_libcsystem_CFLAGS_value=
ac_cv_env_libcsystem_LIBS_set=
ac_cv_env_libcsystem_LIBS_value=
ac_cv_env_libfvalue_CFLAGS_set=
ac_cv_env_libfvalue_CFLAGS_value=
ac_cv_env_libfvalue_LIBS_set=
ac_cv_env_libfvalue_LIBS_value=
ac_cv_env_libhmac_CFLAGS_set=
ac_cv_env_libhmac_CFLAGS_value=
ac_cv_env_libhmac_LIBS_set=
ac_cv_env_libhmac_LIBS_value=
ac_cv_env_libmfcache_CFLAGS_set=
ac_cv_env_libmfcache_CFLAGS_value=
ac_cv_env_libmfcache_LIBS_set=
ac_cv_env_libmfcache_LIBS_value=
ac_cv_env_libmfdata_CFLAGS_set=
ac_cv_env_libmfdata_CFLAGS_value=
ac_cv_env_libmfdata_LIBS_set=
ac_cv_env_libmfdata_LIBS_value=
ac_cv_env_libodraw_CFLAGS_set=
ac_cv_env_libodraw_CFLAGS_value=
ac_cv_env_libodraw_LIBS_set=
ac_cv_env_libodraw_LIBS_value=
ac_cv_env_libsmdev_CFLAGS_set=
ac_cv_env_libsmdev_CFLAGS_value=
ac_cv_env_libsmdev_LIBS_set=
ac_cv_env_libsmdev_LIBS_value=
ac_cv_env_libsmraw_CFLAGS_set=
ac_cv_env_libsmraw_CFLAGS_value=
ac_cv_env_libsmraw_LIBS_set=
ac_cv_env_libsmraw_LIBS_value=
ac_cv_env_libuna_CFLAGS_set=
ac_cv_env_libuna_CFLAGS_value=
ac_cv_env_libuna_LIBS_set=
ac_cv_env_libuna_LIBS_value=
ac_cv_env_openssl_CFLAGS_set=
ac_cv_env_openssl_CFLAGS_value=
ac_cv_env_openssl_LIBS_set=
ac_cv_env_openssl_LIBS_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_env_uuid_CFLAGS_set=
ac_cv_env_uuid_CFLAGS_value=
ac_cv_env_uuid_LIBS_set=
ac_cv_env_uuid_LIBS_value=
ac_cv_env_zlib_CFLAGS_set=
ac_cv_env_zlib_CFLAGS_value=
ac_cv_env_zlib_LIBS_set=
ac_cv_env_zlib_LIBS_value=
ac_cv_func_bindtextdomain=yes
ac_cv_func_chdir=yes
ac_cv_func_close=yes
ac_cv_func_ctime_r=yes
ac_cv_func_fclose=yes
ac_cv_func_feof=yes
ac_cv_func_fgets=yes
ac_cv_func_fopen=yes
ac_cv_func_fread=yes
ac_cv_func_free=yes
ac_cv_func_fseeko64=yes
ac_cv_func_fseeko=yes
ac_cv_func_fstat=yes
ac_cv_func_ftello64=yes
ac_cv_func_ftello=yes
ac_cv_func_ftruncate=yes
ac_cv_func_fwrite=yes
ac_cv_func_getcwd=yes
ac_cv_func_getegid=yes
ac_cv_func_getenv=yes
ac_cv_func_geteuid=yes
ac_cv_func_getopt=yes
ac_cv_func_getrlimit=yes
ac_cv_func_getuid=yes
ac_cv_func_gmtime=yes
ac_cv_func_gmtime_r=yes
ac_cv_func_localeconv=yes
ac_cv_func_localtime=yes
ac_cv_func_localtime_r=yes
ac_cv_func_lseek=yes
ac_cv_func_malloc=yes
ac_cv_func_memchr=yes
ac_cv_func_memcmp=yes
ac_cv_func_memcpy=yes
ac_cv_func_memrchr=no
ac_cv_func_memset=yes
ac_cv_func_mkdir=yes
ac_cv_func_mktime=yes
ac_cv_func_nl_langinfo=yes
ac_cv_func_open=yes
ac_cv_func_posix_fadvise=yes
ac_cv_func_read=yes
ac_cv_func_realloc=yes
ac_cv_func_setlocale=yes
ac_cv_func_setvbuf=yes
ac_cv_func_snprintf=yes
ac_cv_func_sscanf=yes
ac_cv_func_stat=yes
ac_cv_func_strcasecmp=yes
ac_cv_func_strchr=yes
ac_cv_func_strerror_r=yes
ac_cv_func_strerror_r_char_p=no
ac_cv_func_strlen=yes
ac_cv_func_strncasecmp=yes
ac_cv_func_strncmp=yes
ac_cv_func_strncpy=yes
ac_cv_func_strrchr=yes
ac_cv_func_strstr=yes
ac_cv_func_textdomain=yes
ac_cv_func_time=yes
ac_cv_func_uname=yes
ac_cv_func_vfprintf=yes
ac_cv_func_vsnprintf=yes
ac_cv_func_write=yes
ac_cv_have_decl_memrchr=no
ac_cv_have_decl_strerror_r=yes
ac_cv_header_bzlib_h=no
ac_cv_header_cygwin_fs_h=no
ac_cv_header_cygwin_hdreg_h=no
ac_cv_header_dlfcn_h=yes
ac_cv_header_errno_h=yes
ac_cv_header_fcntl_h=yes
ac_cv_header_fuse_h=no
ac_cv_header_glob_h=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_langinfo_h=yes
ac_cv_header_libbfio_h=no
ac_cv_header_libcaes_h=no
ac_cv_header_libcerror_h=no
ac_cv_header_libcfile_h=no
ac_cv_header_libclocale_h=no
ac_cv_header_libcnotify_h=no
ac_cv_header_libcpath_h=no
ac_cv_header_libcsplit_h=no
ac_cv_header_libcstring_h=no
ac_cv_header_libcsystem_h=no
ac_cv_header_libfvalue_h=no
ac_cv_header_libhmac_h=no
ac_cv_header_libintl_h=yes
ac_cv_header_libmfcache_h=no
ac_cv_header_libmfdata_h=no
ac_cv_header_libodraw_h=no
ac_cv_header_libsmdev_h=no
ac_cv_header_libsmraw_h=no
ac_cv_header_libuna_h=no
ac_cv_header_limits_h=yes
ac_cv_header_linux_cdrom_h=yes
ac_cv_header_linux_fs_h=yes
ac_cv_header_linux_hdreg_h=yes
ac_cv_header_linux_usb_ch9_h=yes
ac_cv_header_linux_usbdevice_fs_h=yes
ac_cv_header_locale_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_openssl_evp_h=no
ac_cv_header_openssl_opensslv_h=no
ac_cv_header_osxfuse_fuse_h=no
ac_cv_header_scsi_scsi_h=yes
ac_cv_header_scsi_scsi_ioctl_h=yes
ac_cv_header_scsi_sg_h=yes
ac_cv_header_signal_h=yes
ac_cv_header_stdarg_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_disk_h=no
ac_cv_header_sys_disklabel_h=no
ac_cv_header_sys_ioctl_h=yes
ac_cv_header_sys_resource_h=yes
ac_cv_header_sys_signal_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_syslimits_h=no
ac_cv_header_sys_types_h=yes
ac_cv_header_sys_utsname_h=yes
ac_cv_header_time=yes
ac_cv_header_unistd_h=yes
ac_cv_header_uuid_uuid_h=no
ac_cv_header_varargs_h=no
ac_cv_header_wchar_h=yes
ac_cv_header_wctype_h=yes
ac_cv_header_zlib_h=no
ac_cv_host=i686-pc-linux-gnu
ac_cv_lib_cstring_libcstring_get_version=no
ac_cv_libbfio=local
ac_cv_libbfio_CPPFLAGS=-I../libbfio
ac_cv_libbfio_LIBADD=../libbfio/libbfio.la
ac_cv_libcaes=local
ac_cv_libcaes_CPPFLAGS=-I../libcaes
ac_cv_libcaes_LIBADD=../libcaes/libcaes.la
ac_cv_libcaes_aes=local
ac_cv_libcerror=local
ac_cv_libcerror_CPPFLAGS=-I../libcerror
ac_cv_libcerror_LIBADD=../libcerror/libcerror.la
ac_cv_libcfile=local
ac_cv_libcfile_CPPFLAGS=-I../libcfile
ac_cv_libcfile_LIBADD=../libcfile/libcfile.la
ac_cv_libclocale=local
ac_cv_libclocale_CPPFLAGS=-I../libclocale
ac_cv_libclocale_LIBADD=../libclocale/libclocale.la
ac_cv_libcnotify=local
ac_cv_libcnotify_CPPFLAGS=-I../libcnotify
ac_cv_libcnotify_LIBADD=../libcnotify/libcnotify.la
ac_cv_libcpath=local
ac_cv_libcpath_CPPFLAGS=-I../libcpath
ac_cv_libcpath_LIBADD=../libcpath/libcpath.la
ac_cv_libcrypto=no
ac_cv_libcrypto_evp=no
ac_cv_libcsplit=local
ac_cv_libcsplit_CPPFLAGS=-I../libcsplit
ac_cv_libcsplit_LIBADD=../libcsplit/libcsplit.la
ac_cv_libcstring=local
ac_cv_libcstring_CPPFLAGS=-I../libcstring
ac_cv_libcstring_LIBADD=../libcstring/libcstring.la
ac_cv_libcsystem=local
ac_cv_libcsystem_CPPFLAGS=-I../libcsystem
ac_cv_libcsystem_LIBADD=../libcsystem/libcsystem.la
ac_cv_libfuse=no
ac_cv_libfvalue=local
ac_cv_libfvalue_CPPFLAGS=-I../libfvalue
ac_cv_libfvalue_LIBADD=../libfvalue/libfvalue.la
ac_cv_libhmac=local
ac_cv_libhmac_CPPFLAGS=-I../libhmac
ac_cv_libhmac_LIBADD=../libhmac/libhmac.la
ac_cv_libhmac_md5=local
ac_cv_libhmac_sha1=local
ac_cv_libhmac_sha256=local
ac_cv_libmfcache=local
ac_cv_libmfcache_CPPFLAGS=-I../libmfcache
ac_cv_libmfcache_LIBADD=../libmfcache/libmfcache.la
ac_cv_libmfdata=local
ac_cv_libmfdata_CPPFLAGS=-I../libmfdata
ac_cv_libmfdata_LIBADD=../libmfdata/libmfdata.la
ac_cv_libodraw=local
ac_cv_libodraw_CPPFLAGS=-I../libodraw
ac_cv_libodraw_LIBADD=../libodraw/libodraw.la
ac_cv_libsmdev=local
ac_cv_libsmdev_CPPFLAGS=-I../libsmdev
ac_cv_libsmdev_LIBADD=../libsmdev/libsmdev.la
ac_cv_libsmraw=local
ac_cv_libsmraw_CPPFLAGS=-I../libsmraw
ac_cv_libsmraw_LIBADD=../libsmraw/libsmraw.la
ac_cv_libuna=local
ac_cv_libuna_CPPFLAGS=-I../libuna
ac_cv_libuna_LIBADD=../libuna/libuna.la
ac_cv_libuuid=no
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_FGREP='/bin/grep -F'
ac_cv_path_GMSGFMT=/usr/bin/msgfmt
ac_cv_path_GREP=/bin/grep
ac_cv_path_MSGFMT=/usr/bin/msgfmt
ac_cv_path_MSGMERGE=/usr/bin/msgmerge
ac_cv_path_PKGCONFIG=/usr/bin/pkg-config
ac_cv_path_PYTHON=/usr/bin/python
ac_cv_path_SED=/bin/sed
ac_cv_path_XGETTEXT=/usr/bin/xgettext
ac_cv_path_ac_pt_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_ac_ct_AR=ar
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_DLLTOOL=dlltool
ac_cv_prog_ac_ct_MANIFEST_TOOL=mt
ac_cv_prog_ac_ct_OBJDUMP=objdump
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_ac_ct_STRIP=strip
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_gcc_traditional=no
ac_cv_prog_make_make_set=yes
ac_cv_sizeof_off_t=8
ac_cv_sizeof_size_t=4
ac_cv_struct_tm=time.h
ac_cv_sys_file_offset_bits=64
ac_cv_sys_largefile_CC=no
ac_cv_type_mode_t=yes
ac_cv_type_off64_t=no
ac_cv_type_off_t=yes
ac_cv_type_size32_t=no
ac_cv_type_size64_t=no
ac_cv_type_size_t=yes
ac_cv_type_ssize32_t=no
ac_cv_type_ssize64_t=no
ac_cv_type_ssize_t=yes
ac_cv_type_u64=no
ac_cv_with_adler32=auto-detect
ac_cv_with_bzip2=auto-detect
ac_cv_with_libbfio=auto-detect
ac_cv_with_libcaes=auto-detect
ac_cv_with_libcerror=auto-detect
ac_cv_with_libcfile=auto-detect
ac_cv_with_libclocale=auto-detect
ac_cv_with_libcnotify=auto-detect
ac_cv_with_libcpath=auto-detect
ac_cv_with_libcsplit=auto-detect
ac_cv_with_libcstring=auto-detect
ac_cv_with_libcsystem=auto-detect
ac_cv_with_libfuse=auto-detect
ac_cv_with_libfvalue=auto-detect
ac_cv_with_libhmac=auto-detect
ac_cv_with_libmfcache=auto-detect
ac_cv_with_libmfdata=auto-detect
ac_cv_with_libmsdev=auto-detect
ac_cv_with_libmsraw=auto-detect
ac_cv_with_libodraw=auto-detect
ac_cv_with_libuna=auto-detect
ac_cv_with_libuuid=auto-detect
ac_cv_with_openssl=auto-detect
ac_cv_with_zlib=auto-detect
ac_cv_zlib=no
acl_cv_hardcode_direct=no
acl_cv_hardcode_libdir_flag_spec='${wl}-rpath ${wl}$libdir'
acl_cv_hardcode_libdir_separator=
acl_cv_hardcode_minus_L=no
acl_cv_libext=a
acl_cv_libname_spec='lib$name'
acl_cv_library_names_spec='$libname$shrext'
acl_cv_path_LD=/usr/bin/ld
acl_cv_prog_gnu_ld=yes
acl_cv_rpath=done
acl_cv_shlibext=so
acl_cv_wl=-Wl,
am_cv_CC_dependencies_compiler_type=none
am_cv_pathless_PYTHON=python
am_cv_python_platform=linux2
am_cv_python_pyexecdir='${exec_prefix}/lib/python2.7/dist-packages'
am_cv_python_pythondir='${prefix}/lib/python2.7/dist-packages'
am_cv_python_version=2.7
gt_cv_func_CFLocaleCopyCurrent=no
gt_cv_func_CFPreferencesCopyAppValue=no
gt_cv_func_gnugettext1_libc=yes
lt_cv_ar_at_file=@
lt_cv_archive_cmds_need_lc=no
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file=
lt_cv_ld_reload_flag=-r
lt_cv_nm_interface='BSD nm'
lt_cv_objdir=.libs
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_mainfest_tool=no
lt_cv_prog_compiler_c_o=yes
lt_cv_prog_compiler_pic='-fPIC -DPIC'
lt_cv_prog_compiler_pic_works=yes
lt_cv_prog_compiler_rtti_exceptions=no
lt_cv_prog_compiler_static_works=yes
lt_cv_prog_gnu_ld=yes
lt_cv_sharedlib_from_linklib_cmd='printf %s\n'
lt_cv_shlibpath_overrides_runpath=no
lt_cv_sys_global_symbol_pipe='sed -n -e '\''s/^.*[     ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[     ][     ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p'\'' | sed '\''/ __gnu_lto/d'\'''
lt_cv_sys_global_symbol_to_c_name_address='sed -n -e '\''s/^: \([^ ]*\)[ ]*$/  {\"\1\", (void *) 0},/p'\'' -e '\''s/^[ABCDGIRSTW]* \([^ ]*\) \([^ ]*\)$/  {"\2", (void *) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_c_name_address_lib_prefix='sed -n -e '\''s/^: \([^ ]*\)[ ]*$/  {\"\1\", (void *) 0},/p'\'' -e '\''s/^[ABCDGIRSTW]* \([^ ]*\) \(lib[^ ]*\)$/  {"\2", (void *) \&\2},/p'\'' -e '\''s/^[ABCDGIRSTW]* \([^ ]*\) \([^ ]*\)$/  {"lib\2", (void *) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_cdecl='sed -n -e '\''s/^T .* \(.*\)$/extern int \1();/p'\'' -e '\''s/^[ABCDGIRSTW]* .* \(.*\)$/extern char \1;/p'\'''
lt_cv_sys_max_cmd_len=805306365
lt_cv_to_host_file_cmd=func_convert_file_noop
lt_cv_to_tool_file_cmd=func_convert_file_noop

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /tmp/libewf-20120809/missing --run aclocal-1.11'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE='#'
AMTAR='${SHELL} /tmp/libewf-20120809/missing --run tar'
AR='ar'
AS='as'
AUTOCONF='${SHELL} /tmp/libewf-20120809/missing --run autoconf'
AUTOHEADER='${SHELL} /tmp/libewf-20120809/missing --run autoheader'
AUTOMAKE='${SHELL} /tmp/libewf-20120809/missing --run automake-1.11'
AWK='mawk'
BZIP2_CPPFLAGS=''
BZIP2_LIBADD=''
CC='gcc'
CCDEPMODE='depmode=none'
CFLAGS='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security'
CPP='gcc -E'
CPPFLAGS='-D_FORTIFY_SOURCE=2 -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 -D_FILE_OFFSET_BITS=64'
CYGPATH_W='echo'
DATE=''
DEFS=''
DEPDIR='.deps'
DLLTOOL='dlltool'
DSYMUTIL=''
DUMPBIN=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
FGREP='/bin/grep -F'
GETTEXT_MACRO_VERSION='0.18'
GMSGFMT='/usr/bin/msgfmt'
GMSGFMT_015='/usr/bin/msgfmt'
GREP='/bin/grep'
HAVE_BZIP2='0'
HAVE_INTTYPES_H='1'
HAVE_LIBBFIO='0'
HAVE_LIBCAES='0'
HAVE_LIBCERROR='0'
HAVE_LIBCFILE='0'
HAVE_LIBCLOCALE='0'
HAVE_LIBCNOTIFY='0'
HAVE_LIBCPATH='0'
HAVE_LIBCSPLIT='0'
HAVE_LIBCSTRING='0'
HAVE_LIBCSYSTEM='0'
HAVE_LIBFUSE='0'
HAVE_LIBFVALUE='0'
HAVE_LIBHMAC='0'
HAVE_LIBMFCACHE='0'
HAVE_LIBMFDATA='0'
HAVE_LIBODRAW='0'
HAVE_LIBSMDEV='0'
HAVE_LIBSMRAW='0'
HAVE_LIBUNA='0'
HAVE_LIBUUID='0'
HAVE_LOCAL_LIBBFIO='1'
HAVE_LOCAL_LIBBFIO_FALSE='#'
HAVE_LOCAL_LIBBFIO_TRUE=''
HAVE_LOCAL_LIBCAES='1'
HAVE_LOCAL_LIBCAES_FALSE='#'
HAVE_LOCAL_LIBCAES_TRUE=''
HAVE_LOCAL_LIBCERROR='1'
HAVE_LOCAL_LIBCERROR_FALSE='#'
HAVE_LOCAL_LIBCERROR_TRUE=''
HAVE_LOCAL_LIBCFILE='1'
HAVE_LOCAL_LIBCFILE_FALSE='#'
HAVE_LOCAL_LIBCFILE_TRUE=''
HAVE_LOCAL_LIBCLOCALE='1'
HAVE_LOCAL_LIBCLOCALE_FALSE='#'
HAVE_LOCAL_LIBCLOCALE_TRUE=''
HAVE_LOCAL_LIBCNOTIFY='1'
HAVE_LOCAL_LIBCNOTIFY_FALSE='#'
HAVE_LOCAL_LIBCNOTIFY_TRUE=''
HAVE_LOCAL_LIBCPATH='1'
HAVE_LOCAL_LIBCPATH_FALSE='#'
HAVE_LOCAL_LIBCPATH_TRUE=''
HAVE_LOCAL_LIBCSPLIT='1'
HAVE_LOCAL_LIBCSPLIT_FALSE='#'
HAVE_LOCAL_LIBCSPLIT_TRUE=''
HAVE_LOCAL_LIBCSTRING='1'
HAVE_LOCAL_LIBCSTRING_FALSE='#'
HAVE_LOCAL_LIBCSTRING_TRUE=''
HAVE_LOCAL_LIBCSYSTEM='1'
HAVE_LOCAL_LIBCSYSTEM_FALSE='#'
HAVE_LOCAL_LIBCSYSTEM_TRUE=''
HAVE_LOCAL_LIBFVALUE='1'
HAVE_LOCAL_LIBFVALUE_FALSE='#'
HAVE_LOCAL_LIBFVALUE_TRUE=''
HAVE_LOCAL_LIBHMAC='1'
HAVE_LOCAL_LIBHMAC_FALSE='#'
HAVE_LOCAL_LIBHMAC_TRUE=''
HAVE_LOCAL_LIBMFCACHE='1'
HAVE_LOCAL_LIBMFCACHE_FALSE='#'
HAVE_LOCAL_LIBMFCACHE_TRUE=''
HAVE_LOCAL_LIBMFDATA='1'
HAVE_LOCAL_LIBMFDATA_FALSE='#'
HAVE_LOCAL_LIBMFDATA_TRUE=''
HAVE_LOCAL_LIBODRAW='1'
HAVE_LOCAL_LIBODRAW_FALSE='#'
HAVE_LOCAL_LIBODRAW_TRUE=''
HAVE_LOCAL_LIBSMDEV='1'
HAVE_LOCAL_LIBSMDEV_FALSE='#'
HAVE_LOCAL_LIBSMDEV_TRUE=''
HAVE_LOCAL_LIBSMRAW='1'
HAVE_LOCAL_LIBSMRAW_FALSE='#'
HAVE_LOCAL_LIBSMRAW_TRUE=''
HAVE_LOCAL_LIBUNA='1'
HAVE_LOCAL_LIBUNA_FALSE='#'
HAVE_LOCAL_LIBUNA_TRUE=''
HAVE_MEMWATCH_FALSE=''
HAVE_MEMWATCH_TRUE=''
HAVE_OFF64_T='0'
HAVE_OPENSSL_EVP_H='0'
HAVE_PYTHON_FALSE=''
HAVE_PYTHON_TRUE=''
HAVE_SIZE32_T='0'
HAVE_SIZE64_T='0'
HAVE_SSIZE32_T='0'
HAVE_SSIZE64_T='0'
HAVE_STDINT_H='1'
HAVE_SYS_TYPES_H='1'
HAVE_V1_API=''
HAVE_V1_API_FALSE=''
HAVE_V1_API_TRUE=''
HAVE_WCHAR_H='0'
HAVE_WIDE_CHARACTER_TYPE='0'
HAVE_ZLIB='0'
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
INTLLIBS=''
INTL_MACOSX_LIBS=''
LD='/usr/bin/ld'
LDFLAGS='-Wl,-Bsymbolic-functions -Wl,-z,relro'
LEX='${SHELL} /tmp/libewf-20120809/missing --run flex'
LEXLIB=''
LEX_OUTPUT_ROOT=''
LIBBFIO_CPPFLAGS='-I../libbfio'
LIBBFIO_LIBADD='../libbfio/libbfio.la'
LIBCAES_CPPFLAGS='-I../libcaes'
LIBCAES_LIBADD='../libcaes/libcaes.la'
LIBCERROR_CPPFLAGS='-I../libcerror'
LIBCERROR_LIBADD='../libcerror/libcerror.la'
LIBCFILE_CPPFLAGS='-I../libcfile'
LIBCFILE_LIBADD='../libcfile/libcfile.la'
LIBCLOCALE_CPPFLAGS='-I../libclocale'
LIBCLOCALE_LIBADD='../libclocale/libclocale.la'
LIBCNOTIFY_CPPFLAGS='-I../libcnotify'
LIBCNOTIFY_LIBADD='../libcnotify/libcnotify.la'
LIBCPATH_CPPFLAGS='-I../libcpath'
LIBCPATH_LIBADD='../libcpath/libcpath.la'
LIBCRYPTO_CPPFLAGS=''
LIBCRYPTO_LIBADD=''
LIBCSPLIT_CPPFLAGS='-I../libcsplit'
LIBCSPLIT_LIBADD='../libcsplit/libcsplit.la'
LIBCSTRING_CPPFLAGS='-I../libcstring'
LIBCSTRING_LIBADD='../libcstring/libcstring.la'
LIBCSYSTEM_CPPFLAGS='-I../libcsystem'
LIBCSYSTEM_LIBADD='../libcsystem/libcsystem.la'
LIBDL_LIBADD=''
LIBEWF_DLL_IMPORT=''
LIBFUSE_CPPFLAGS=''
LIBFUSE_LIBADD=''
LIBFVALUE_CPPFLAGS='-I../libfvalue'
LIBFVALUE_LIBADD='../libfvalue/libfvalue.la'
LIBHMAC_CPPFLAGS='-I../libhmac'
LIBHMAC_LIBADD='../libhmac/libhmac.la'
LIBICONV='-liconv'
LIBINTL=''
LIBMFCACHE_CPPFLAGS='-I../libmfcache'
LIBMFCACHE_LIBADD='../libmfcache/libmfcache.la'
LIBMFDATA_CPPFLAGS='-I../libmfdata'
LIBMFDATA_LIBADD='../libmfdata/libmfdata.la'
LIBOBJS=''
LIBODRAW_CPPFLAGS='-I../libodraw'
LIBODRAW_LIBADD='../libodraw/libodraw.la'
LIBS=''
LIBSMDEV_CPPFLAGS='-I../libsmdev'
LIBSMDEV_LIBADD='../libsmdev/libsmdev.la'
LIBSMRAW_CPPFLAGS='-I../libsmraw'
LIBSMRAW_LIBADD='../libsmraw/libsmraw.la'
LIBTOOL='$(SHELL) $(top_builddir)/libtool'
LIBTOOL_DEPS='./ltmain.sh'
LIBUNA_CPPFLAGS='-I../libuna'
LIBUNA_LIBADD='../libuna/libuna.la'
LIBUUID_CPPFLAGS=''
LIBUUID_LIBADD=''
LIPO=''
LN_S='ln -s'
LTLIBICONV='-liconv'
LTLIBINTL=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /tmp/libewf-20120809/missing --run makeinfo'
MANIFEST_TOOL=':'
MEMWATCH_CPPFLAGS=''
MEMWATCH_LIBADD=''
MKDIR_P='/bin/mkdir -p'
MSGFMT='/usr/bin/msgfmt'
MSGFMT_015='/usr/bin/msgfmt'
MSGMERGE='/usr/bin/msgmerge'
NM='/usr/bin/nm -B'
NMEDIT=''
OBJDUMP='objdump'
OBJEXT='o'
OTOOL64=''
OTOOL=''
PACKAGE='libewf'
PACKAGE_BUGREPORT='joachim.metz@gmail.com'
PACKAGE_NAME='libewf'
PACKAGE_STRING='libewf 20120809'
PACKAGE_TARNAME='libewf'
PACKAGE_URL=''
PACKAGE_VERSION='20120809'
PATH_SEPARATOR=':'
PKGCONFIG='/usr/bin/pkg-config'
PKG_CONFIG='/usr/bin/pkg-config'
PKG_CONFIG_LIBDIR=''
PKG_CONFIG_PATH=''
POSUB='po'
PWD='/tmp/libewf-20120809'
PYTHON='/usr/bin/python'
PYTHON_CPPFLAGS='-I/usr/include/python2.7'
PYTHON_EXEC_PREFIX='${exec_prefix}'
PYTHON_EXTRA_LIBS=''
PYTHON_LDFLAGS=''
PYTHON_PLATFORM='linux2'
PYTHON_PREFIX='${prefix}'
PYTHON_SITE_PKG=''
PYTHON_VERSION='2.7'
RANLIB='ranlib'
SED='/bin/sed'
SET_MAKE=''
SHELL='/bin/bash'
STATIC_LDFLAGS=''
STRIP='strip'
USE_NLS='yes'
VERSION='20120809'
XGETTEXT='/usr/bin/xgettext'
XGETTEXT_015='/usr/bin/xgettext'
XGETTEXT_EXTRA_OPTIONS=''
YACC='yacc'
YFLAGS=''
ZLIB_CPPFLAGS=''
ZLIB_LIBADD=''
ac_ct_AR='ar'
ac_ct_CC='gcc'
ac_ct_DUMPBIN=''
am__EXEEXT_FALSE=''
am__EXEEXT_TRUE=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE='#'
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
ax_bzip2_pc_libs_private=''
ax_bzip2_spec_build_requires=''
ax_bzip2_spec_requires=''
ax_libbfio_pc_libs_private=''
ax_libbfio_spec_build_requires=''
ax_libbfio_spec_requires=''
ax_libcaes_pc_libs_private=''
ax_libcaes_spec_build_requires=''
ax_libcaes_spec_requires=''
ax_libcerror_pc_libs_private=''
ax_libcerror_spec_build_requires=''
ax_libcerror_spec_requires=''
ax_libcfile_pc_libs_private=''
ax_libcfile_spec_build_requires=''
ax_libcfile_spec_requires=''
ax_libclocale_pc_libs_private=''
ax_libclocale_spec_build_requires=''
ax_libclocale_spec_requires=''
ax_libcnotify_pc_libs_private=''
ax_libcnotify_spec_build_requires=''
ax_libcnotify_spec_requires=''
ax_libcpath_pc_libs_private=''
ax_libcpath_spec_build_requires=''
ax_libcpath_spec_requires=''
ax_libcrypto_pc_libs_private=''
ax_libcrypto_spec_build_requires=''
ax_libcrypto_spec_requires=''
ax_libcsplit_pc_libs_private=''
ax_libcsplit_spec_build_requires=''
ax_libcsplit_spec_requires=''
ax_libcstring_pc_libs_private=''
ax_libcstring_spec_build_requires=''
ax_libcstring_spec_requires=''
ax_libcsystem_pc_libs_private=''
ax_libcsystem_spec_build_requires=''
ax_libcsystem_spec_requires=''
ax_libfuse_pc_libs_private=''
ax_libfuse_spec_build_requires=''
ax_libfuse_spec_requires=''
ax_libfvalue_pc_libs_private=''
ax_libfvalue_spec_build_requires=''
ax_libfvalue_spec_requires=''
ax_libhmac_pc_libs_private=''
ax_libhmac_spec_build_requires=''
ax_libhmac_spec_requires=''
ax_libmfcache_pc_libs_private=''
ax_libmfcache_spec_build_requires=''
ax_libmfcache_spec_requires=''
ax_libmfdata_pc_libs_private=''
ax_libmfdata_spec_build_requires=''
ax_libmfdata_spec_requires=''
ax_libodraw_pc_libs_private=''
ax_libodraw_spec_build_requires=''
ax_libodraw_spec_requires=''
ax_libsmdev_pc_libs_private=''
ax_libsmdev_spec_build_requires=''
ax_libsmdev_spec_requires=''
ax_libsmraw_pc_libs_private=''
ax_libsmraw_spec_build_requires=''
ax_libsmraw_spec_requires=''
ax_libuna_pc_libs_private=''
ax_libuna_spec_build_requires=''
ax_libuna_spec_requires=''
ax_libuuid_pc_libs_private=''
ax_libuuid_spec_build_requires=''
ax_libuuid_spec_requires=''
ax_zlib_pc_libs_private=''
ax_zlib_spec_build_requires=''
ax_zlib_spec_requires=''
ax_zlib_static_spec_requires=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias='i686-linux-gnu'
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
bzip2_CFLAGS=''
bzip2_LIBS=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
fuse_CFLAGS=''
fuse_LIBS=''
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${prefix}/share/info'
install_sh='${SHELL} /tmp/libewf-20120809/install-sh'
libbfio_CFLAGS=''
libbfio_LIBS=''
libcaes_CFLAGS=''
libcaes_LIBS=''
libcerror_CFLAGS=''
libcerror_LIBS=''
libcfile_CFLAGS=''
libcfile_LIBS=''
libclocale_CFLAGS=''
libclocale_LIBS=''
libcnotify_CFLAGS=''
libcnotify_LIBS=''
libcpath_CFLAGS=''
libcpath_LIBS=''
libcsplit_CFLAGS=''
libcsplit_LIBS=''
libcstring_CFLAGS=''
libcstring_LIBS=''
libcsystem_CFLAGS=''
libcsystem_LIBS=''
libdir='${exec_prefix}/lib'
libewf_spec_build_requires=''
libewf_spec_requires=''
libexecdir='${prefix}/lib/libewf'
libfvalue_CFLAGS=''
libfvalue_LIBS=''
libhmac_CFLAGS=''
libhmac_LIBS=''
libmfcache_CFLAGS=''
libmfcache_LIBS=''
libmfdata_CFLAGS=''
libmfdata_LIBS=''
libodraw_CFLAGS=''
libodraw_LIBS=''
libsmdev_CFLAGS=''
libsmdev_LIBS=''
libsmraw_CFLAGS=''
libsmraw_LIBS=''
libuna_CFLAGS=''
libuna_LIBS=''
localedir='${datarootdir}/locale'
localstatedir='/var'
mandir='${prefix}/share/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
openssl_CFLAGS=''
openssl_LIBS=''
pdfdir='${docdir}'
pkgpyexecdir='${pyexecdir}/libewf'
pkgpythondir='${pythondir}/libewf'
prefix='/usr'
program_transform_name='s,x,x,'
psdir='${docdir}'
pyexecdir='${exec_prefix}/lib/python2.7/dist-packages'
pythondir='${prefix}/lib/python2.7/dist-packages'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='/etc'
target_alias=''
uuid_CFLAGS=''
uuid_LIBS=''
zlib_CFLAGS=''
zlib_LIBS=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "libewf"
#define PACKAGE_TARNAME "libewf"
#define PACKAGE_VERSION "20120809"
#define PACKAGE_STRING "libewf 20120809"
#define PACKAGE_BUGREPORT "joachim.metz@gmail.com"
#define PACKAGE_URL ""
#define PACKAGE "libewf"
#define VERSION "20120809"
#define _FILE_OFFSET_BITS 64
#define STDC_HEADERS 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_MEMORY_H 1
#define HAVE_STRINGS_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_DLFCN_H 1
#define LT_OBJDIR ".libs/"
#define ENABLE_NLS 1
#define HAVE_GETTEXT 1
#define HAVE_DCGETTEXT 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define SIZEOF_OFF_T 8
#define SIZEOF_SIZE_T 4
#define HAVE_LIBINTL_H 1
#define HAVE_LIMITS_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_FCLOSE 1
#define HAVE_FEOF 1
#define HAVE_FGETS 1
#define HAVE_FOPEN 1
#define HAVE_FREAD 1
#define HAVE_FSEEKO 1
#define HAVE_FSEEKO64 1
#define HAVE_FWRITE 1
#define HAVE_VFPRINTF 1
#define HAVE_FREE 1
#define HAVE_MALLOC 1
#define HAVE_MEMCMP 1
#define HAVE_MEMCPY 1
#define HAVE_MEMSET 1
#define HAVE_REALLOC 1
#define HAVE_PRINTF_JD 1
#define HAVE_PRINTF_ZD 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_WCHAR_H 1
#define HAVE_WCTYPE_H 1
#define HAVE_FGETS 1
#define HAVE_MEMCHR 1
#define HAVE_MEMCMP 1
#define HAVE_MEMCPY 1
#define HAVE_MEMRCHR 1
#define HAVE_SNPRINTF 1
#define HAVE_SSCANF 1
#define HAVE_STRCASECMP 1
#define HAVE_STRCHR 1
#define HAVE_STRLEN 1
#define HAVE_STRNCASECMP 1
#define HAVE_STRNCMP 1
#define HAVE_STRNCPY 1
#define HAVE_STRRCHR 1
#define HAVE_STRSTR 1
#define HAVE_VSNPRINTF 1
#define HAVE_DECL_MEMRCHR 0
#define HAVE_LOCAL_LIBCSTRING 1
#define HAVE_STDARG_H 1
#define HAVE_DECL_STRERROR_R 1
#define HAVE_STRERROR_R 1
#define HAVE_LOCAL_LIBCERROR 1
#define HAVE_LANGINFO_H 1
#define HAVE_LOCALE_H 1
#define HAVE_GETENV 1
#define HAVE_LOCALECONV 1
#define HAVE_SETLOCALE 1
#define HAVE_NL_LANGINFO 1
#define HAVE_LANGINFO_CODESET 1
#define HAVE_LOCAL_LIBCLOCALE 1
#define HAVE_STDARG_H 1
#define HAVE_ERRNO_H 1
#define HAVE_LOCAL_LIBCNOTIFY 1
#define HAVE_LOCAL_LIBCSPLIT 1
#define HAVE_LOCAL_LIBUNA 1
#define HAVE_ERRNO_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_FCNTL_H 1
#define HAVE_UNISTD_H 1
#define HAVE_CLOSE 1
#define HAVE_FSTAT 1
#define HAVE_FTRUNCATE 1
#define HAVE_LSEEK 1
#define HAVE_OPEN 1
#define HAVE_READ 1
#define HAVE_WRITE 1
#define HAVE_FCLOSE 1
#define HAVE_FEOF 1
#define HAVE_FOPEN 1
#define HAVE_FREAD 1
#define HAVE_FSEEKO 1
#define HAVE_FSEEKO64 1
#define HAVE_FTELLO 1
#define HAVE_FTELLO64 1
#define HAVE_FWRITE 1
#define HAVE_STAT 1
#define HAVE_LOCAL_LIBCFILE 1
#define HAVE_ERRNO_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_CHDIR 1
#define HAVE_GETCWD 1
#define HAVE_MKDIR 1
#define HAVE_MKDIR 1
#define HAVE_MKDIR_MODE 1
#define HAVE_LOCAL_LIBCPATH 1
#define HAVE_LOCAL_LIBBFIO 1
#define HAVE_LOCAL_LIBFVALUE 1
#define TIME_WITH_SYS_TIME 1
#define HAVE_TIME 1
#define HAVE_LOCAL_LIBMFCACHE 1
#define HAVE_LOCAL_LIBMFDATA 1
#define HAVE_LOCAL_LIBHMAC 1
#define HAVE_LOCAL_LIBCAES 1
#define TIME_WITH_SYS_TIME 1
#define HAVE_LOCALTIME 1
#define HAVE_LOCALTIME_R 1
#define HAVE_MKTIME 1
#define HAVE_BINDTEXTDOMAIN 1
#define HAVE_ERRNO_H 1
#define HAVE_FCNTL_H 1
#define HAVE_UNISTD_H 1
#define HAVE_SYS_STAT_H 1
#define TIME_WITH_SYS_TIME 1
#define HAVE_GLOB_H 1
#define HAVE_SIGNAL_H 1
#define HAVE_SYS_SIGNAL_H 1
#define HAVE_CLOSE 1
#define HAVE_FSTAT 1
#define HAVE_FTRUNCATE 1
#define HAVE_LSEEK 1
#define HAVE_OPEN 1
#define HAVE_READ 1
#define HAVE_STAT 1
#define HAVE_WRITE 1
#define HAVE_LOCALTIME 1
#define HAVE_LOCALTIME_R 1
#define HAVE_MKTIME 1
#define HAVE_CTIME_R 1
#define HAVE_CTIME_R 1
#define HAVE_GMTIME 1
#define HAVE_GMTIME_R 1
#define HAVE_TIME 1
#define HAVE_GETOPT 1
#define HAVE_SETVBUF 1
#define HAVE_BINDTEXTDOMAIN 1
#define HAVE_TEXTDOMAIN 1
#define HAVE_LOCAL_LIBCSYSTEM 1
#define HAVE_LOCAL_LIBODRAW 1
#define HAVE_ERRNO_H 1
#define HAVE_FCNTL_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_LINUX_FS_H 1
#define HAVE_SYS_IOCTL_H 1
#define HAVE_LINUX_HDREG_H 1
#define HAVE_SCSI_SCSI_H 1
#define HAVE_SCSI_SCSI_IOCTL_H 1
#define HAVE_SCSI_SG_H 1
#define HAVE_LINUX_CDROM_H 1
#define HAVE_LINUX_USBDEVICE_FS_H 1
#define HAVE_LINUX_USB_CH9_H 1
#define HAVE_CLOSE 1
#define HAVE_FSTAT 1
#define HAVE_FTRUNCATE 1
#define HAVE_LSEEK 1
#define HAVE_OPEN 1
#define HAVE_READ 1
#define HAVE_STAT 1
#define HAVE_WRITE 1
#define HAVE_POSIX_FADVISE 1
#define HAVE_POSIX_FADVISE 1
#define HAVE_DECL_STRERROR_R 1
#define HAVE_STRERROR_R 1
#define HAVE_LOCAL_LIBSMDEV 1
#define HAVE_LOCAL_LIBSMRAW 1
#define HAVE_SYS_RESOURCE_H 1
#define HAVE_SYS_UTSNAME_H 1
#define HAVE_GETEGID 1
#define HAVE_GETEUID 1
#define HAVE_GETRLIMIT 1
#define HAVE_GETUID 1
#define HAVE_UNAME 1

configure: exit 1
dh_auto_configure: ./configure --build=i686-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/libewf --disable-maintainer-mode --disable-dependency-tracking --enable-python returned exit code 1
make[1]: *** [override_dh_auto_configure] Error 25
make[1]: Leaving directory `/tmp/libewf-20120809'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

How to solve it? Thank you very much!

---

