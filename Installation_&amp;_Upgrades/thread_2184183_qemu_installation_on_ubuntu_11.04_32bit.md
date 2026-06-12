---
title: "qemu installation on ubuntu 11.04 32bit"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by linuxque on 2013-10-28
Hi,
  I am trying to install qemu 1.6.1 on ubuntu 11.04 - 32bit machine. Started with numerous dependencies issue which most have been resolved like autoconf, automake etc.  Now I am stuck at pixman, wherein when I configure and run make, receiving make errors as follows. Kindly guide.

***_Output of make_***
root@ubuntu:/opt/qemu-1.6.1# make
  GEN   config-host.h
(cd pixman; CFLAGS="-O2 -D_FORTIFY_SOURCE=2 -g  -fPIC -m32  " /opt/qemu-1.6.1/pixman/configure  --disable-gtk --disable-shared --enable-static)
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for getisax... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking size of long... 4
checking whether __SUNPRO_C is declared... no
checking whether __amd64 is declared... no
checking for perl... /usr/bin/perl
checking for -fvisibility... yes
checking for -xldscope (Sun compilers)... no
checking whether to use MMX intrinsics... yes
checking whether to use SSE2 intrinsics... yes
checking whether to use VMX/Altivec intrinsics... no
checking whether to use ARM SIMD assembler... no
checking whether to use ARM NEON assembler... no
checking whether to use GNU-style inline assembler... yes
/opt/qemu-1.6.1/pixman/configure: line 12670: PKG_PROG_PKG_CONFIG: command not found
/opt/qemu-1.6.1/pixman/configure: line 12672: syntax error near unexpected token `gtk+-2.0,'
/opt/qemu-1.6.1/pixman/configure: line 12672: `   PKG_CHECK_EXISTS(gtk+-2.0, enable_gtk=yes, enable_gtk=no)'
make: *** [pixman/Makefile] Error 2

Thanks,
Linuxque

---

### Post by sudodus on 2013-10-28
Ubuntu 11.04 is long past end of life, and you cannot expect installing and updating to work properly. For example, there are no securiy updates.

Is there some particular reason, that you use that version? Otherwise I suggest that you backup all your personal files (and important settings) and make a fresh install of 12.04 LTS (or maybe the newest version 13.10).

---

