---
title: "App installation help!"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by spot135 on 2011-03-14
Hi,

I'm having problems installing a program and I was wondering (hoping more) that somebody could help. I'm a final year student and as part of my project I need to use a product called quicknet, which I'm finding impossible to install! It is distributed as source code with little to no installation guide and I'm stuck... 

Ok so I'm running 10.4 lucid Lynx

I download unpackage etc and create a build folder, from here I configure, which seems to run ok, and then make which returns this error:

../QN_args2.cc: In function ‘int cleNextPattern(const char*, char*, const char**)’:
../QN_args2.cc:169: error: invalid conversion from ‘const char*’ to ‘char*’
../QN_args2.cc:175: error: invalid conversion from ‘const char*’ to ‘char*’
../QN_args2.cc: In function ‘int cleScanTime(const char*, float*)’:
../QN_args2.cc:217: error: invalid conversion from ‘const char*’ to ‘char*’
make: *** [QN_args2.o] Error 1

After looking on the internet I found this is to do with the gcc & g++ I'm using (which 4.4.3). So I started trying to go through the code and change the errors with limited success, main problem being there's LOADS of them and I've never programed in c++ before.

So I presume the only alternative is downgrading to a version of gcc which hopefully the program will compile with. However, I couldn't seem to get any version to install. 

I finally got 4.1 installed from synaptic (the earliest one on there) and if I:

"ls /usr/bin/gcc*" && "ls /usr/bin/g++*" it gives 

/usr/bin/gcc  /usr/bin/gcc-4.1  /usr/bin/gcc-4.4  /usr/bin/gccbug-4.1
&
/usr/bin/g++  /usr/bin/g++-4.1  /usr/bin/g++-4.4

so they are installed, but when I say CC="usr/bin/gcc-4.1" CXX="usr/bin/g++-4.1" or any combination I can think of it gives me this error:

scott@ubuntu:~/quicknet/quicknet/build$ ../configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... usr/bin/gcc-4.1
checking whether the C compiler works... no
configure: error: in `/home/scott/quicknet/quicknet/build':
configure: error: C compiler cannot create executables
See `config.log' for more details


So there I am...Any help will be massively appreciated! I have been at this for hours and hours lol.


Scott

---

### Post by spot135 on 2011-03-14
Fixed it...

Just thought I'd put how

```
rm /usr/bin/gcc
```

```
ln -s /usr/bin/gcc-x.x /usr/bin/gcc
```

as for the quicknet, used gcc & g++ version 4.0.3

---

