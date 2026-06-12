---
title: "[SOLVED] Compiling xvidcap"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by Jesdisciple on 2008-06-13
I'm trying to install [xvidcap]("http://xvidcap.sourceforge.net/") to get screen-capture recordings for troubleshooting purposes.  [http://ubuntuforums.org/archive/index.php/t-91073.html](http://ubuntuforums.org/archive/index.php/t-91073.html) got me where I am, but now I seem to be missing some dependencies...```
$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for gawk... (cached) mawk
checking for a sed that does not truncate output... /bin/sed
checking for bc... /usr/bin/bc
checking for X... no
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
checking for docbook2x-man... no
configure: Couldn't find docbook2x-man to generate current man pages. Will try db2x_docbook2man.
checking for db2x_docbook2man... no
configure: Couldn't find neither docbook2x-man nor db2x_docbook2man to generate current man pages. Will install pre-generated ones if present.
checking for xml2po... /usr/bin/xml2po
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

$ sudo apt-get install gtk+-2.0
[sudo] password for chris:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtk+-2.0
```

Please help me again...  I promise it won't be the last time.  :lol:

---

### Post by Partyboi2 on 2008-06-14
try
```
sudo apt-get install libgtk2.0-dev libglade2-dev libglib2.0-dev
```then rerun ./configure

---

### Post by Jesdisciple on 2008-06-14
One more - 'libXmu' - and that exact name wasn't found in the repositories...  EDIT: But libxmu-dev was, and that worked.

EDIT2: Wait, how am I supposed to run it?

Thanks for your time!  :)

---

### Post by Partyboi2 on 2008-06-14
In a terminal type
```
xvidcap
```

---

### Post by Jesdisciple on 2008-06-16
Sorry for my delay in posting; I was visiting my parents.```
chris@Jesdisciple-laptop:~/Documents/xvidcap-1.1.6$ xvidcap
bash: xvidcap: command not found
```I think I did everything the INSTALL file said to...

---

### Post by Partyboi2 on 2008-06-16
The easiest way and recommended way to install it is to use the ubuntu repos's. Make sure you have multiverse enabled in Software Sources (System>Admin>Software Sources) 
```
sudo apt-get install xvidcap
```

If for some reason you prefer to continue compilng from source make sure you have finished the compiling stages. 
./configure
make
sudo make install

---

### Post by Jesdisciple on 2008-06-16
```
E: Couldn't find package xvidcap
```

But the problem must have been that I was cleaning it after installing...  The instructions suggested that as if it would only free hard disk space.  Compiling without cleaning got it.  Thanks!

---

### Post by Partyboi2 on 2008-06-16
> E: Couldn't find package xvidcap
Just to clarify this package is in the hardy repos, so if you are using a earlier release of ubuntu you won't find it in the repo's. My mistake I should have asked you what version you were using.
Good to see you managed to get it installed. :)

---

