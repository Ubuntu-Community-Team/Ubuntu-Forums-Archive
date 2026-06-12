---
title: "sdl-config error when compiling DOSbox 0.70"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by anthony62490 on 2011-05-08
Trying to compile DOSbox version [_[COLOR="Blue"]0.70[/COLOR]_]("http://sourceforge.net/projects/dosbox/files/dosbox/0.70/"). Apparently this is the only version that can run Privateer flawlessly.

Problem is, when I extract the source and try to './configure', I get an error that SDL 1.2 is not installed.

```
anthony@anthony-1010:~/Games/DOS/dosbox-0.70$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
[B]checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.[/B]
configure: error: *** SDL version 1.2.0 not found!
```

I have searched everywhere to find out how to fix this error. I don't see any relevant packages in the repos.

This one has me stumped. Any ideas?

---

### Post by lloyd_b on 2011-05-08
Take a look at [this link]("http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development") - it contains decent instructions for setting up to develop stuff using SDL.

Lloyd B.

---

