---
title: "development on unbuntu?"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by seancarr on 2005-02-08
***EDIT: Problem fixed. Didn't notice the howto guide... 8-[ ***

ok, this is my first time installing ubuntu. And im quite confused or maybe I just havent payed attention...i dont know...but i am used to having all of my base systems (gentoo mainly) coming with development packages (compilers etc.) defaultly. Does Ubuntu not have them in the base system? and if not, what exactly (since they are usually already installed) would i need to compile source packages?

Ive already tried compiling an engine theme for GTK and this was the error i received:

root@tux:/home/sean/themeing/clearlooks-engine-0.2.2 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

thanks for your help.

---

### Post by trivialpackets on 2005-02-08
I believe Ubuntu does come with GCC, but there are many more available.  enable the universal repositors  in /etc/apt/sources.list by uncommenting them.
then....
apt-get update
apt-cache search filename
apt-get install resultofabovesearc -C /opt/ 
                                                       or wherever youw ant it to go.

I like anjuta for a GUI for C++.  Or you could use synaptic, either option is doable.
Good luck!

---

### Post by trivialpackets on 2005-02-08
I'm sorry, if GCC is stating it's not there, just do above and get the GCC off apt.

---

