---
title: "Installing iScan-2.3.0 (epson rx520)"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by ughi on 2006-11-20
Hi folks!
Here is my problem: I'm trying to install iScan-2.3.0 tool for my Epson Stylus Photo RX520 multifunction printer. Somebody knows how to go ahead? What I have to install? The following box is the output from './configure' command.
Thanks a lot!!
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking C++ ABI version... 1002
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... checking for gtk+... sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
yes
checking GTK_CFLAGS... sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found

checking GTK_LIBS... sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found

checking for imlibgdk... Package imlibgdk was not found in the pkg-config search path. Perhaps you should add the directory containing `imlibgdk.pc' to the PKG_CONFIG_PATH environment variable No package 'imlibgdk' found
configure: error: Library requirements (imlibgdk) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

---

### Post by jeffbarish on 2006-11-27
I have the same problem.  I'd love to see an answer to this question.

---

### Post by luxor on 2006-12-02
If you have an i386 system, [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) has the packages for download.

Your compile problem results from some libraries not being present. 
You need to do the following:

sudo apt-get install libgtk-dev
sudo apt-get install imlibgdk
sudo apt-get install gdk-imlib-dev

I also had to edit lib/imgstream.hh and change line 46 from
#include <ltdl.h>    TO   include <../libltdl/ltdl.h>
It then builds fine, but I don't have a frontend since I'm building on PPC.  Anyone have any ideas to proceed from here?

Any help would be much appreciated.

---

