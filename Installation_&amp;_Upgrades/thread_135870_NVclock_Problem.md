---
title: "NVclock Problem"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by Coolit on 2006-02-24
Hi All,

I've been trying to install nvclock 0.7 using apt, it installs fine but I get a segmentation error when I try to run it from the cmd line. I decided to compile version 8.0b (latest) and remove 0.7, But I'm getting the following errors, does anyone know how to solve this?

andy@Coolit1:~/nvclock0.8b$ ./autogen.sh autoconf: Undefined macros:
configure.in:119:        AC_MSG_NOTICE([no X Window System found])

I have also tried "./configure --prefix=/usr/local" as posted in another thread but receive a no GCC error even though gcc is installed,

andy@Coolit1:~/nvclock0.8b$ ./configure --prefix=/usr/local
loading cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot cre ate executables.


Thanks in advance :)

EDIT: Im using 64bit Ubuntu

---

### Post by Coolit on 2006-02-24
OK I've made some progress but the X error is now stopping me :( the QT error wont matter as Im not going to use the QT interface.

andy@Coolit1:~/nvclock0.8b$ ./configure --prefix=/usr/local loading cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for library containing getopt_long... none required
checking for getopt.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.4.0... checking for X... libraries /usr/X11R6/lib, headers
checking QTDIR... *** Can't find qt header/library directories, you can fix this using two ways depending on your system:
*** - set QTDIR or use -with-qtdir=DIR option
*** - use --with-qt-includes=DIR or --with-qt-libraries=DIR to set the include/library directory
./configure: line 2921: syntax error near unexpected token `no'
./configure: line 2921: `        AC_MSG_NOTICE(no X Window System found)'

EDIT: I had a look at the configure file in an editor, line 2921 is just after it looks for NV-CONTROL, so it looks like it cant find NV-CONTROL, now.. nvidia-settings is working fine so I guess that means NV-CONTROL is also, hmm....

---

