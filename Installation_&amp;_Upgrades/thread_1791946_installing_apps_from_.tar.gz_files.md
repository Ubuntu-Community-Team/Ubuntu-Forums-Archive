---
title: "installing apps from .tar.gz files"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by subchief on 2011-06-27
Hey Guys,
I have downloaded tvtime from their website as a .tar.gz file and would like to install it.
I have extracted the files to my home folder and renamed the folder to tvtime-1.0
Then in the terminal, i ran the following commands

cd ~/tvtime-1.0

./configure --prefix=/usr --sysconfdir=/etc

make

However i got the following messge

make: *** No targets specified and no makefile found.  Stop.


Can anyone Help?
Thanks!

---

### Post by oldos2er on 2011-06-27
Can you post the output from the ./configure command?

---

### Post by subchief on 2011-06-28
> **oldos2er said:**
> Can you post the output from the ./configure command?
here's the output...



checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... yes
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
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g++... no

---

### Post by sanderd17 on 2011-06-28
It seems you are missing some build tools. Try installing the build essentials:

```

sudo apt-get install build-essentials

```

---

### Post by sanderd17 on 2011-06-28
BTW, is there any special reason that you want to compile it? It is also in the repositories:

```

sudo apt-get install tvtime

```

---

### Post by subchief on 2011-06-28
> **sanderd17 said:**
> BTW, is there any special reason that you want to compile it? It is also in the repositories:

```

sudo apt-get install tvtime

```

Well i hadnt updates my repositories for some reason...so i couldnt install it. However i did update and install the application but i thot the knowledge would be nice...
Thanks alot!

---

### Post by subchief on 2011-06-28
> **sanderd17 said:**
> It seems you are missing some build tools. Try installing the build essentials:

```

sudo apt-get install build-essentials

```
 
and the code given above doesnt work...
though this does...
```

sudo apt-get install build-essential

``` 

Thanks again!

---

### Post by sanderd17 on 2011-06-28
> **subchief said:**
> and the code given above doesnt work...
though this does...
```

sudo apt-get install build-essential

``` 

Thanks again!

Oh damn, I should always check something before I type it.

---

### Post by subchief on 2011-06-28
> **sanderd17 said:**
> Oh damn, I should always check something before I type it.

No worries man...You did help and its the gesture that counts ain't it?:)

---

