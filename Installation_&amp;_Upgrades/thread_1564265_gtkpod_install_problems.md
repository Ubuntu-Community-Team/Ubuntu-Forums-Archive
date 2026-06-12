---
title: "gtkpod install problems"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by guriinii on 2010-08-30
I've been trying to install gtkpod. Then I get this error:
```
:~/Desktop/gtkpod-1.0.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking whether NLS is requested... yes
checking for intltool >= 0.33... 0.40.6 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
configure: error: in `/home/greenys/Desktop/gtkpod-1.0.0':
configure: error: *** Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
See `config.log' for more details.
```

But:
```
:~/Desktop/gtkpod-1.0.0$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
```

I've tried building from source and run into a multitude of other problems with pango. 

Can anyone please advise?

---

### Post by SabreWolfy on 2011-06-11
Why is this marked as Solved? It seems to come from the CrunchBang forums:

[http://crunchbanglinux.org/forums/topic/9330/gtkpod-install-problems/]("http://crunchbanglinux.org/forums/topic/9330/gtkpod-install-problems/")

or 

[http://crunchbanglinux.org/forums/topic/9330/solved-gtkpod-install-problems/]("http://crunchbanglinux.org/forums/topic/9330/solved-gtkpod-install-problems/")

---

