---
title: "Net-snmp installation problem"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Scatarro on 2009-12-19
Hi all,

 I'm trying to install net-snmp ver. 5.5, the latest stable version. I downloaded from [http://net-snmp.sourceforge.net/download.html](http://net-snmp.sourceforge.net/download.html), and the application itself installs OK, i.e. the commands 
```

cd net-snmp-5.5
./configure --with-perl-modules --enable-shared
make
make test
make install 
```run fine, with no errors. However, when I cd to the included perl directory (i.e. that comes with the download) and try to do:

```
/usr/bin/perl Makefile.PL
make 
make test

```These are the results:

```
Failed Test  Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/async.t     127 32512    20   35  3-20
t/bulkwalk.t               62   53  2-10 13-31 34-40 42 44-51 53-61
t/get.t                    17   15  2-16
t/getnext.t                 9    7  2-3 5-9
t/notify.t                 10    3  7 9-10
t/session.t                 5    2  2 5
t/set.t                     7    1  2
Failed 7/10 test scripts. 99/175 subtests failed.
Files=10, Tests=175, 267 wallclock secs ( 1.14 cusr +  0.21 csys =  1.35 CPU)

```Furthermore, when I lunch commands, i.e. snmpwalk, I got this error:

```
snmpwalk: error while loading shared libraries: libnetsnmp.so.20: cannot open shared object file: No such file or directory
```Some info about my pc:
```
$ locate libnetsnmp
/usr/lib/libnetsnmp.so.15
/usr/lib/libnetsnmp.so.15.1.0
/usr/lib/libnetsnmpagent.so.15
/usr/lib/libnetsnmpagent.so.15.1.0
/usr/lib/libnetsnmphelpers.so.15
/usr/lib/libnetsnmphelpers.so.15.1.0
/usr/lib/libnetsnmpmibs.so.15
/usr/lib/libnetsnmpmibs.so.15.1.0
/usr/lib/libnetsnmptrapd.so.15
/usr/lib/libnetsnmptrapd.so.15.1.0


$:gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

$:cat /etc/issue
Ubuntu 9.10 \n \l


```Please advice me how can I handle this problem.

Thanks.
Pietro.

SOLUTION: ok I found the error. There were an older installation and a lot of conflicts. Cleaning the machine and reinstall the software solved the problem. 
Thanks anyway. :)

---

### Post by Goldiescorpio on 2010-11-26
Hi Scatarro,

Could you please tell me what cleaning up you did: Directories? commands ran?

I'm having the same problem, also did some cleaning and re-install, but I could not resolve the issue.

Thanks in advance!

Grtz!

Goldie

---

