---
title: "Install Help"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by sfarber on 2007-07-06
Hello.

Every source I download and try to compile and install, there is a problem.
When i run the configure script it stops and say :

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

What is wrong on my computer?

Shay.

---

### Post by fearevilleet on 2007-07-06
try,

```
sudo apt-get install gcc
```

---

### Post by sfarber on 2007-07-07
I have tried that.
It says :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What else can I do?

---

