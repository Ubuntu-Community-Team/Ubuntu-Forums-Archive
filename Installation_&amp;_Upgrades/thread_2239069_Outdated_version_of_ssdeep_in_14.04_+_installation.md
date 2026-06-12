---
title: "Outdated version of ssdeep in 14.04 + installation problems"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by alex238 on 2014-08-11
Hello everybody!

I've just installed ssdeep via apt-get on Ubuntu 14.04. But the version 2.7 is far outdated ([http://packages.ubuntu.com/search?keywords=ssdeep&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=ssdeep&searchon=names&suite=all&section=all)), since the developer released 2.10 in 2013 ([http://ssdeep.sourceforge.net](http://ssdeep.sourceforge.net)). Would it be possible to include the recent one in the Ubuntu packages?

I tried to install the 2.10 by myself compiling the source code, but every time I tried the configure script failed. This is the log of the whole procedure:

```
$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... no, using cp -pR
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking /usr/local/include
checking /opt/local/include
checking /sw/include
checking whether byte ordering is bigendian... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for inttypes.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for sys/types.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for unistd.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking sys/disk.h usability... no
checking sys/disk.h presence... no
checking for sys/disk.h... no
checking for inttypes.h... (cached) yes
checking for sys/mount.h... yes
checking for _LARGEFILE_SOURCE value needed for large files... no
checking that generated files are newer than configure... done
configure: creating ./config.status
./config.status: line 2231: syntax error: unexpected end of file

```

I think it has something to do with the absense of sys/disk.h file because the log says it's missing. But I'm not sure. I googled it already, but wasn't able to find anything useful on that topic. Does anyone have an idea?

Thanks in advance!

---

### Post by tuhlbox on 2014-09-17
Had the exact same problem, but it had nothing to do with the absence of sys/disk.h. I nailed it down to an incompatibility between the version of autoconf that the build configuration was generated with and the installed version on my system.

All I had to do was:

1. Install libtoolize
```
sudo apt-get install libtoolize
```

2. Run autoreconf in the build directory
```
cd ssdeep-2.11/
autoreconf
```

3. Configure, make and install
```
./configure
make
sudo make install
```

Hope this will solve it for you, too. :)

Cheers,
Thomas

---

### Post by ian-weisser on 2014-09-18
> **alex238 said:**
> Would it be possible to include the recent one in the Ubuntu packages?

Sure.

See [https://tracker.debian.org/pkg/ssdeep](https://tracker.debian.org/pkg/ssdeep) for the progress getting 2.11 into Debian. And for the reasons why releases after 2.7 were not used.

After it's in Debian Unstable, it will be automatically imported into the next release of Ubuntu.

It's too late for 14.10, Debian import freeze is already past.
If people help test 2.11 in Debian and get it into Unstable, it can show up in Ubuntu 15.04.

After 2.11 has been released in Ubuntu, it's eligible for backporting into previous versions. That's a different and easier process.

---

