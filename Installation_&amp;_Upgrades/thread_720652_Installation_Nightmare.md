---
title: "Installation Nightmare"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by Mikrotik_T on 2008-03-10
Hi All

I am new, but what is new?
I am trying to install prozilla-2.0.0.tar.gz but have no luck. Heeeeelllllppppp!!!!!!!!!
I start of with "./configure" and then it does its thing but at the end it gives an error:

tommy@EliteIT:~/Desktop/prozilla-2.0.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
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
checking for C++ compiler default output file name... [COLOR="Red"]**configure: error: C++ compiler cannot create executables**[/COLOR]
See `config.log' for more details.

what am I doing wrong???
Please if any one can help.:confused:

---

### Post by forestpixie on 2008-03-10
try installing build essential
```
sudo apt-get install build-essential
```

and trying again

---

### Post by kellemes on 2008-03-10
You need to understand you're not installing a program, you're compiling a program.
For this you need to have the tools installed.
Previous poster gives the solution..

---

