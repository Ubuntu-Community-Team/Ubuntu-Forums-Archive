---
title: "need help installing program"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by gamepanther on 2010-09-15
hi i have installed abgx 360 and am now following the directions on how to install the gui but it isnt working fergal@fergal-laptop:~$ cd Desktop
fergal@fergal-laptop:~/Desktop$ cd abgx360gui-1.0.2/
fergal@fergal-laptop:~/Desktop/abgx360gui-1.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
fergal@fergal-laptop:~/Desktop/abgx360gui-1.0.2$ make
make: *** No targets specified and no makefile found. Stop.

---

### Post by oldos2er on 2010-09-15
```
sudo apt-get install build-essential
```

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

