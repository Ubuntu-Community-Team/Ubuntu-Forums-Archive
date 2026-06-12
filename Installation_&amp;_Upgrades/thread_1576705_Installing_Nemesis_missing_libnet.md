---
title: "Installing Nemesis missing libnet"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Jrider04 on 2010-09-17
Hi, I have been trying to install nemesis for the last 6 hours. Every time I run the ./configure it indicates that it can not locate the libnet libraries. I have libnet installed along with libnet1-dev. 

The findings are below. I appreciate any help that you can provide

```

justin@justin-desktop:~$ sudo -s -H
[sudo] password for justin: 
root@justin-desktop:/home/justin# cd Downloads/nemesis-1.4
root@justin-desktop:/home/justin/Downloads/nemesis-1.4# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
root@justin-desktop:/home/justin/Downloads/nemesis-1.4# whereis libnet
libnet: /usr/lib/libnet.la /usr/lib/libnet.so /usr/lib/libnet.a /usr/include/libnet.h /usr/include/libnet

```

---

### Post by 1d3m on 2010-09-23
the same case bro. check it:

solvet it !! (on ubuntu lucid)
1. nemesis depends on the libnet in its 0 version (obsolete by the way, 
but doesnt matter). First, we have to download the next libnet suite:

(a) libnet0_1.0.2a-7_i386.deb-----------http://packages.ubuntu.com/hardy/i386/libnet0/download
(b) libpcap0.8-dev_1.0.0-6_i386.deb--http://packages.ubuntu.com/hardy/i386/libpcap0.8/download
(c) libnet0-dev_1.0.2a-7_i386.deb-----
[http://packages.ubuntu.com/jaunty/i386/libnet0-dev/download](http://packages.ubuntu.com/jaunty/i386/libnet0-dev/download)

2. The (c) packet (libnet0-dev) depends on the (a) and (b) packets.
so, we have to install both first, then...

3. install the (c) packet.

4. the ./configure on nemesis folder.

5. next, make command.

6. when introduce make install command, maybe the next error will be display:

/usr/bin/install: cannot create regular file `/usr/local/bin/nemesis': Permission denied

so we have to give it appropiate permission:

$ sudo rm chmod 777 /usr/local/nemesis

now:

$ sudo make install

....as the dwarf of twin peaks movie would say "Let's rock"....

thks

---

### Post by saporati on 2010-11-14
> **1d3m said:**
> the same case bro. check it:

solvet it !! (on ubuntu lucid)
1. nemesis depends on the libnet in its 0 version (obsolete by the way, 
but doesnt matter). First, we have to download the next libnet suite:

(a) libnet0_1.0.2a-7_i386.deb-----------http://packages.ubuntu.com/hardy/i386/libnet0/download
(b) libpcap0.8-dev_1.0.0-6_i386.deb--http://packages.ubuntu.com/hardy/i386/libpcap0.8/download
(c) libnet0-dev_1.0.2a-7_i386.deb-----
[http://packages.ubuntu.com/jaunty/i386/libnet0-dev/download](http://packages.ubuntu.com/jaunty/i386/libnet0-dev/download)

2. The (c) packet (libnet0-dev) depends on the (a) and (b) packets.
so, we have to install both first, then...

3. install the (c) packet.



Great!! the quoted  part worked for me, then I installed the nemesis*.deb package successfully. 
Thanks a lot
S.

---

