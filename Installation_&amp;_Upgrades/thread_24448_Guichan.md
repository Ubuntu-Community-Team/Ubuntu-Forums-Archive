---
title: "Guichan"
date: 2005-04-06
forum: Installation &amp; Upgrades
---

### Post by Dko on 2005-04-06
Hi.  Im preaty new to linux and ive been trying to get a game up and running called The Mana World.   It sayed it required Guichan witch ive dled and attempting to install.  BUt I seam to get this when I type ./configure:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/jesse/Desktop/guichan-0.3.0-src/missing: /home/jesse/Desktop/guichan-0.3.0-src/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

What can I do to make configure work right? Please help this newb.

---

### Post by dataw0lf on 2005-04-07
sudo apt-get install build-essential

---

### Post by Dko on 2005-04-07
Ok that seams to work fine. But now when I run configure I get something like this.
config.status: error: cannot find input file: include/guichan/opengl/Makefile.in  Ive tried placing the Makefile.in in those directory and it gets past them only to add one more subdirectory which I have to add another Makefile.in. Anyway I can stop this? >.<


EDIT: Gehh now I get this instead after doing a bunch of copying and pasting and can't figure out where this would be. 

config.status: error: cannot find input file: include/config.hpp.in

---

