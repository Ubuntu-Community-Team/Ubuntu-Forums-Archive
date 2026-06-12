---
title: "configure : error C++"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by Rival_Azeez on 2015-03-20
hello... i have a problem with inkscape installation
take a look

rival_azeez@rival-azeez-AO722:~/inkscape$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking how to create a pax tar archive... gnutar
checking for style of include used by make... GNU
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether the C++ compiler works... no
configure: error: in `/home/rival_azeez/inkscape':
configure: error: C++ compiler cannot create executables
See `config.log' for more details

it says "configure: error: C++ compiler cannot create executables". What's going on? Please help

---

### Post by steeldriver on 2015-03-20
Hello and welcome to the forums

Your system doesn't appear to have a C++ compiler installed on it - unless you need to use a different compiler specifically, you probably just need to install the g++ package or (to add a more complete build environment), the build-essential metapackage

```

sudo apt-get install build-essential

```

FYI you shouldn't use sudo with ./configure when building stuff in your own home directory - it will leave hard-to-remove root owned files there

---

### Post by Impavidus on 2015-03-21
You need a compiler, as noted by steeldriver. Then you'll probably also need some development versions of libraries. The configure script ought to tell you which.

But inkscape is available from the repositories. Do you absolutely need the latest version? It's much easier to install from the repos.

---

### Post by Rival_Azeez on 2015-03-26
Thanks to steeldriver and Impavidus

Lately I had a problem when i tried to update via terminal. Then I choosed best server, and it worked. Thanks. :)

---

