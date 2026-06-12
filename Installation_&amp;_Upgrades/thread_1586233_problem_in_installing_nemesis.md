---
title: "problem in installing nemesis"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by piyush.neo on 2010-10-01
i am using ubuntu 10.04.

when i as trying to install nemesis its showing error that libnet is missing
```

root@piyush-laptop:~/Downloads/rawsocket/packet injector/tool/nemesis-1.4# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/piyush/Downloads/rawsocket/packet: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
checking for gcc option to accept ANSI C... none needed
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for an ANSI C-conforming const... yes
checking for gawk... (cached) gawk
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for fabs in -lm... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking for hstrerror in -lresolv... yes
checking for libnet_build_ip in -lnet... no

   ERROR!  Libnet library not found, go get it from
   http://www.packetfactory.net/projects/libnet/
   or use the --with-libnet-* options, if you have it installed
   in unusual place


```**Though the Version 1.1.4-2(libnet1) has already been installed on machine.**
Then i manually downloaded the libnet library from
[http://packetfactory.openwall.net/projects/libnet/index.html](http://packetfactory.openwall.net/projects/libnet/index.html) but still the same error.

Here is the instruction for installing it.
```

Installing Nemesis on UNIX-like systems:
========================================

Installing Nemesis on UNIX-like systems is a straightforward process that 
closely resembles installing any other piece of software using GNU autotools.  
Before attempting to install Nemesis, ensure that libnet-1.0.2a is installed.

The following steps are all that is needed to compile and install Nemesis:
1. ./configure
2. make
3. make install
4. examine the nemesis man pages
5. enjoy.

When compiling the following switches are available:
----------------------------------------------------

`--enable-debug'
     Enable debugging options (bugreports and developers only).

`--enable-profile'
     Enable code profiling options (developers only).

`--with-libnet-includes=DIR'
     If the configuration script can't find the libnet include files on its
     own, the path can be set manually with this switch.  Do not include
     a trailing / when specifying the include path. 

     Example:

     --with-libnet-includes=/usr/local/libnet/include

`--with-libnet-libraries=DIR'
     If the configuration script can't find the libnet library files on its
     own, the path can be set manually with this switch.  Do not include
     a trailing / when specifying the library path.

     Example:

     --with-libnet-libraries=/usr/local/libnet/lib

``````
piyush@piyush-laptop:~$ whereis libnet
libnet: /usr/lib/libnet.a /usr/lib/libnet.la /usr/lib/libnet.so /usr/include/libnet.h /usr/include/libnet

```

I have already tried installing with few "--with-libnet-includes" option...
Plz help me to figure out the problem.

---

### Post by oldos2er on 2010-10-01
You installed libnet1-dev?

---

### Post by piyush.neo on 2010-10-02
> **oldos2er said:**
> You installed libnet1-dev?
Yes, i have already installed it.

---

### Post by hawk_eyes on 2010-10-02
I issued the command with appropriate paths.

$whereis libnet
libnet: /usr/lib/libnet.a /usr/lib/libnet.la /usr/lib/libnet.so /usr/include/libnet /usr/include/libnet.h

$./configure --with-libnet-includes=/usr/include --with-libnet-libraries=/usr/lib

 Even then i am getting the same error:

checking for libnet_build_ip in -lnet... no

   ERROR!  Libnet library not found, go get it from
   [http://www.packetfactory.net/projects/libnet/](http://www.packetfactory.net/projects/libnet/)
   or use the --with-libnet-* options, if you have it installed
   in unusual place

Did i give the correct path options?

i just now followed the advice from the below link and installed nemesis successfully :)


[http://forum.ivorde.ro/checking-for-libnet-build-ip-in-lnet-no-error-libnet-library-not-found-t135.html](http://forum.ivorde.ro/checking-for-libnet-build-ip-in-lnet-no-error-libnet-library-not-found-t135.html)

---

### Post by piyush.neo on 2010-10-02
> **hawk_eyes said:**
> i just now followed the advice from the below link and installed nemesis successfully :)


[http://forum.ivorde.ro/checking-for-libnet-build-ip-in-lnet-no-error-libnet-library-not-found-t135.html](http://forum.ivorde.ro/checking-for-libnet-build-ip-in-lnet-no-error-libnet-library-not-found-t135.html)

I have followed your advice but still problem persist. After installing libnet by ur link
```

root@piyush-laptop:~/Libnet-1.0.2a# whereis libnet-config
libnet-config: /usr/bin/libnet-config /usr/share/man/man1/libnet-config.1.gz
```
Its not in \usr\lib ...is it a problem??

---

### Post by Shideneyu on 2013-03-10
I use to resolve all of my compiling trouble. I resolved this one in 45 minutes. I was stucked with the same problem as piyush-neo.

This has done the trick: ./configure --with-libnet-includes=/home/shideneyu/Libnet-1.0.2a/include  --with-libnet-libraries=/'/home/shideneyu/Libnet-1.0.2a/lib'
Replace the path to your libnet folders. Notice that I've install libnet-1.0.2a but it seems that the routes haven't been updated.
I got a x64 architecture, no further change to make it work ;)

Have a nice day :D !

---

### Post by oldos2er on 2013-03-10
Old thread closed, please don't bump old threads.

---

