---
title: "installing xnec2c"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by dhirajkhanna on 2008-03-11
I have been trying to install xnec2c but haven't succeeded so far. I downloaded the debian package xnec2c_1.0b3-3_i386.deb and then from the terminal i typed 

sudo dpkg -i xnec2c_1.0b3-3_i386.deb (after navigating to the correct directory. The error that I get is:

Selecting previously deselected package xnec2c.
(Reading database ... 122895 files and directories currently installed.)
Unpacking xnec2c (from xnec2c_1.0b3-3_i386.deb) ...
dpkg: dependency problems prevent configuration of xnec2c:
 xnec2c depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu10.
dpkg: error processing xnec2c (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xnec2c

Can somebody help me with this dependency issue please?
Thanks

---

