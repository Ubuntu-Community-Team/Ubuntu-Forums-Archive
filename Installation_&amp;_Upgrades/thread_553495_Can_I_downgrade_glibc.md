---
title: "Can I downgrade glibc?"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by rg_stephens on 2007-09-17
I'm a student and I REALLY need Matlab on my computer.  I got it installed, but I'm getting error messages. The tech support guy told me that my older version of Matlab is incompatible with glibc. Here is what he said: I quote:
> 
Hello Robert,

It appears that the glibc libraries in the version of Linux you are
 running are too new for MATLAB Student Version Release 14 with
 Service
 Pack 3.  You will need a glibc library of 2.3.2.

What do I need to do? I decided to post here before I do something to mess up my computer. Here's my version info:
```
beto@beto-laptop:~$ /lib/libc.so.6
GNU C Library stable release version 2.5, by Roland McGrath et al.
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.1.2 (Ubuntu 4.1.2-0ubuntu4).
Compiled on a Linux >>2.6.15.7<< system on 2007-04-04.
Available extensions:
        crypt add-on version 2.1 by Michael Glad and others
        GNU Libidn by Simon Josefsson
        GNU libio by Per Bothner
        NIS(YP)/NIS+ NSS modules 0.19 by Thorsten Kukuk
        Native POSIX Threads Library by Ulrich Drepper et al
        BIND-8.2.3-T5B
Thread-local storage support included.
For bug reporting instructions, please see:
<http://www.gnu.org/software/libc/bugs.html>.
beto@beto-laptop:~$ 
```

---

### Post by rg_stephens on 2007-09-18
I guess what I am asking is, is it possible to install an older version of glibc along with the newer version?

---

