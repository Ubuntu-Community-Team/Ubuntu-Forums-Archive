---
title: "Libc6 woes (please be gentle)"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by dburgan on 2006-10-02
Hello all, I'm new to the Ubuntu way of doing things having recently defected from the Fedora world and I love Ubuntu.  At least things work most of the time, unlike Fedora.  :-)

OK so I think I did something really dumb and I'm not sure how to recover.  I am trying out some rather experimental audio software, including running Windows audio software under WINE, and somewhere during the process I upgraded my libc6 without realizing what a problem I was creating.

Searching these forums, I found some helpful threads.  Based upon these, I have tried 'downgrading' to the previous version of libc6, the one that Ubuntu installed, by forcing the specific version number, using apt-get, e.g.:

sudo apt-get install libc6=2.3.6-0ubuntu20

This command seems to work okay except apt-get tells me it is about to REMOVE 268 packages, clearing up 734MB of disk space, and asks if I am sure.  To which I respond "no" of course, since I'm not sure at all.

Is it really going to blow away 734MB worth of programs off my filesystem?  Is there any less painful way to downgrade my libc6?

Any tips?  I'm not a Linux newbie but I am new to Ubuntu and frankly don't want to make this problem worse than it already is .... help!  Thanks for any help anyone can provide!

Below is the output of "sudo apt-cache show libc6" in case it is helpful ...

> 
Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 23340
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: glibc
Version: 2.4-1ubuntu10
Replaces: ldso (<= 1.9.11-9), timezone, timezones, gconv-modules, libtricks, lib c6-bin, netkit-rpc, netbase (<< 4.0)
Provides: glibc-2.3.6-2, glibc-2.3.5-3
Depends: locales (>= 2.3.11)
Suggests: locales, glibc-doc
Conflicts: strace (<< 4.0-0), libnss-db (<= 2.2-6.1.1), timezone, timezones, gco nv-modules, libtricks, libc6-doc, libc5 (<< 5.4.33-7), libpthread0 (<< 0.7-10), libc6-bin, libwcsmbs, apt (<< 0.3.0), libglib1.2 (<< 1.2.1-2), netkit-rpc, wine (<< 0.0.20031118-1), cyrus-imapd (<< 1.5.19-15), e2fsprogs (<< 1.35-7), initrd-t ools (<< 0.1.84.1), libterm-readline-gnu-perl (<< 1.15-2)
Conffiles:
 /etc/init.d/glibc.sh febdb7acbbd106c3a02415770e5599b8
 /etc/ld.so.conf.d/i486-linux-gnu 36f09aeeab18f6af453d0a1db0a0942c
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
X-Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>

Package: libc6
Priority: required
Section: base
Installed-Size: 9932
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: glibc
Version: 2.3.6-0ubuntu20
Replaces: ldso (<= 1.9.11-9), timezone, timezones, gconv-modules, libtricks, lib c6-bin, netkit-rpc, netbase (<< 4.0)
Provides: glibc-2.3.5-0ubuntu1
Depends: locales (>= 2.3.11)
Suggests: locales, glibc-doc
Conflicts: strace (<< 4.0-0), libnss-db (<= 2.2-6.1.1), timezone, timezones, gco nv-modules, libtricks, libc6-doc, libc5 (<< 5.4.33-7), libpthread0 (<< 0.7-10), libc6-bin, libwcsmbs, apt (<< 0.3.0), libglib1.2 (<< 1.2.1-2), netkit-rpc, wine (<< 0.0.20031118-1), cyrus-imapd (<< 1.5.19-15), initrd-tools (<< 0.1.79), e2fsp rogs (<< 1.35-7), libterm-readline-gnu-perl (<< 1.15-2)
Filename: pool/main/g/glibc/libc6_2.3.6-0ubuntu20_i386.deb
Size: 4587534
MD5sum: 8996b5468767af7c2995da09b7c1eb15
Description: GNU C Library: Shared libraries and Timezone data
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
 Timezone data is also included.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


---

