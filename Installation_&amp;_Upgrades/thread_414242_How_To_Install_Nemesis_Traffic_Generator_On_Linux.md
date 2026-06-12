---
title: "How To Install Nemesis Traffic Generator On Linux"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-04-19
****

HI,.

Actually I am trying to install Nemesis on Linux and it requires Libnet and I have installed it .

**The problem is when I type ./configure command it could not locate libnet, may be libnet is in another directory **
error is :

checking for libnet_build_ip in -lnet... no

   ERROR!  Libnet library not found, go get it from
   [http://www.packetfactory.net/projects/libnet/](http://www.packetfactory.net/projects/libnet/)
   or use the --with-libnet-* options, if you have it installed
   in unusual place

and then I tried typing whereis command:

xxx@xxx-xxxx:/home/vamsi/Desktop/nemesis-1.4beta3# **whereis libnet**
libnet: /usr/lib/libnet.a /usr/lib/libnet.la /usr/lib/libnet.so /usr/include/libnet /usr/include/libnet.h /usr/man/man3/libnet.3

How to tell nemesis where is libnet .

**Installing Nemesis on UNIX-like systems:(procedure which i followed)**
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

`--with-libnet-includes=DIR'
     If the configuration script can't find the libnet include files on its
     own, the path can be set manually with this switch.

`--with-libnet-libraries=DIR'
     If the configuration script can't find the libnet library files on its
     own, the path can be set manually with this switch.

---

