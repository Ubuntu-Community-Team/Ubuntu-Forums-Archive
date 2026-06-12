---
title: "Can't install apache2-dbg - unable to locate package"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by bphillips2 on 2014-03-16
I am trying to debug a coredump issue with Apache.  I have been following a [tutorial]("http://sysadmin.carlusgg.com/?p=197") on using gbd to backtrace the problem.  In the tutorial I need to install apache2-dbg using
> apt-get install apache2-dbg

However, when I run that command I get the following output
> justin@ubuntu:/etc/apt$ sudo apt-get install apache2-dbgReading package lists... Done
Building dependency tree       
Reading state information... Done
E: **Unable to locate package apache2-dbg**
justin@ubuntu:/etc/apt$ 

Everywhere I have read says to use that same command to download the package.  Is there some other command I can use? Or something else I need to do to make that command work?

Thanks,

---

### Post by steeldriver on 2014-03-16
Based on a package search at [packages.ubuntu.com]("http://packages.ubuntu.com/saucy/apache2-dbg") it appears that apache2-dbg is only available for 13.10 and later - it's not obvious what package (if any) provides the dbg binaries in earlier releases

---

### Post by bphillips2 on 2014-03-17
Thanks for the reply.  I was able to get the gdb program to work without this package by changing my permissions in my core dump file.

---

