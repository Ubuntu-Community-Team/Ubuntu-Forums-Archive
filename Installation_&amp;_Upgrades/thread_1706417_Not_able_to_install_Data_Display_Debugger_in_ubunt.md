---
title: "Not able to install Data Display Debugger in ubuntu 10.4"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by tirthpandya on 2011-03-13
Hi,

I am trying to install DDD on ubuntu 10.4. Downloaded the  tar.gz file and followed the instructions given on DDD web page.

But  I am not able to install DDD. While trying to do './configure  && make' I get the following error. It says c++ is not working  and is not able to create executables. 
I have g++ installed and I successfully create excutables from .cpp  files. I've also checked the CXX variable and it is set to /usr/bin  where g++ is expected to be placed.


[B]root@tirth-laptop:/home/tirth/Downloads/ddd-3.2.1#  ./configure && make
loading cache ./config.cache
checking host system type...  i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking  build system type... i686-pc-linux-gnu
checking for a BSD compatible  install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether  make sets ${MAKE}... yes
checking for working aclocal... missing
checking  for working autoconf... missing
checking for working automake...  missing
checking for working autoheader... missing
checking for working  makeinfo... missing
checking whether make sets ${MAKE}... (cached)  yes
checking for gcc... gcc
checking whether the C compiler (gcc  )  works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking  whether we are using GNU C... yes
checking whether gcc accepts -g...  yes
checking for POSIXized ISC... no
checking whether the C  compiler (gcc) compiles and links a simple C program... yes
checking for c++... /usr/bin/
checking whether the C++ compiler  (/usr/bin/  ) works... no
configure: error: installation or  configuration problem: C++ compiler cannot create executables.[/B]

Please  look into this issue and advice.

Prompt response would be highly appreciated.

Thanks,
Tirth

---

### Post by lkraemer on 2011-03-14
Typically you need to install build-essential, and the headers for the
kernel you are running before you try a Compile.

```

uname -r

```
will tell you the kernel you are running

```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the necessary stuff for Compiles.

You then download the source and extract
```

cd /path/to/source
tar xvf packagename.tar.gz

```
Then to compile the source:
```

cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```

make clean won't remove anything on the first compile, but will clean up
on successive compiles.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


BUT.......it's in the repos.  Why not just use Synaptic to install it from the repos versus a Compile of source?
SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER


lk

---

