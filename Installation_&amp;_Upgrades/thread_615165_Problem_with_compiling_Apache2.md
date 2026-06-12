---
title: "Problem with compiling Apache2"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by pawulon86 on 2007-11-16
I try to compile Apache 2.2.6. This what I'm doing
1. I unpack sources to catalog "/home/pawel/apache/serwer"
2. I use "sudo -s" to get root permissions.
3. I run ./configure and I get this:

root@pawel-desktop:~/apache/serwer# sudo ./configure
[INDENT]
    checking for chosen layout... Apache
    checking for working mkdir -p... yes
    checking build system type... i686-pc-linux-gnulibc1
    checking host system type... i686-pc-linux-gnulibc1
    checking target system type... i686-pc-linux-gnulibc1

    Configuring Apache Portable Runtime library ...

    checking for APR... reconfig
    configuring package in srclib/apr now
    checking build system type... i686-pc-linux-gnulibc1
    checking host system type... i686-pc-linux-gnulibc1
    checking target system type... i686-pc-linux-gnulibc1
    Configuring APR library
    Platform: i686-pc-linux-gnulibc1
    checking for working mkdir -p... yes
    APR Version: 1.2.11
    checking for chosen layout... apr
    checking for gcc... gcc
    checking for C compiler default output file name... configure: error: C compiler cannot create executables
    See `config.log' for more details.
    configure failed for srclib/apr[/INDENT]

I tried to use prefix option in ./configure but It hasn't help.  

I tried that all just after I had installed Ubuntu and all upgrades.

Anybody knows what is the problem?

---

### Post by pawulon86 on 2007-11-17
Ok, I know what I was doing wrong.
I haven't installed build-essential before. After I had done it there were no problems.

---

