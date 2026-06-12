---
title: "Oracle unusable after upgrade to 12.04"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by hma.istsupport on 2012-07-25
I was running on 10.10 and installed 11g R1. I had some development on Pro*C. Everything was running fine.
Just for curious about the newer versions I upgraded to 11.04 and the pre-compilation started to fail due to a few header file missing, like stdarg.h and libaio.h

Since anyway screwed ;-) I upgraded twice and reached now at 12.04. Now the problem is when I try to install it says about missing packages. Please see the image for missing packages. Please see attached file for the available package configurations.
When I check, 
(1)some of the packages are installed, with a higher version, but still not accepted.
(2)Some packages I am not able to install. Please someone help me on this.
    (a)glibc
    (b)compatlibstdc++
    (c)elfutilslibelf
    (e)elfutilslibelfdevel
    (f)glibccommon
    (g)glibcdevel
    (h)glibcheaders
    (i)gccc++
    (j)libaiodevel
    (k)libgcc
    (l)libstdc++
    (m)libstdc++devel
    (n)sysstat
    (o)unixODBCdevel

After this I am facing a few makefile errors as below. Once the package errors are resolved, I will retry and post all the makefile errors.

Thanks everyone
Adarsh

---

