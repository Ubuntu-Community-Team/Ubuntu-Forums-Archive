---
title: "Error in make EMD package.&quot; File is attached&quot;"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by hamzeh2 on 2013-08-01
Attachment is related to molecular dynamics simulations. Two packages are required to install this program. gsl and boost file system. I've installed the package, but I get this error.

root@parsa-45pc:/home/parsa/EMD/EMD# [COLOR=#ff0000]./configure[/COLOR]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/quaternion/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@parsa-45pc:/home/parsa/EMD/EMD#[COLOR=#ff0000] make[/COLOR]
make  all-recursive
make[1]: Entering directory `/home/parsa/EMD/EMD'
Making all in src
make[2]: Entering directory `/home/parsa/EMD/EMD/src'
Making all in quaternion
make[3]: Entering directory `/home/parsa/EMD/EMD/src/quaternion'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/parsa/EMD/EMD/src/quaternion'
make[3]: Entering directory `/home/parsa/EMD/EMD/src'
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT moluniverse_comp.o -MD -MP -MF .deps/moluniverse_comp.Tpo -c -o moluniverse_comp.o moluniverse_comp.cpp
In file included from /usr/include/c++/4.7/ext/hash_map:61:0,
                 from cell_grid.h:30,
                 from moluniverse.h:44,
                 from moluniverse_comp.h:52,
                 from moluniverse_comp.cpp:23:
/usr/include/c++/4.7/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
moluniverse_comp.cpp: In function ‘double emd::uni::eval_number_of_regions(unsigned int, double, double, double)’:
[COLOR=#ff0000]moluniverse_comp.cpp:848:7: error: expected initializer before ‘j’
moluniverse_comp.cpp:853:15: error: ‘j’ was not declared in this scope
moluniverse_comp.cpp:853:20: error: ‘jend’ was not declared in this scope[/COLOR]
[COLOR=#4b0082]make[3]: *** [moluniverse_comp.o] Error 1
make[3]: Leaving directory `/home/parsa/EMD/EMD/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/parsa/EMD/EMD/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/parsa/EMD/EMD'[/COLOR]
make: *** [all] Error 2

---

### Post by dino99 on 2013-08-01
the red lines teach you what you need to fix first :P

---

