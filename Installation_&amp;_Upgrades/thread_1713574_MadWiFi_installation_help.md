---
title: "MadWiFi installation help"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by briggin on 2011-03-24
Hi everyone

I was hoping some people on here could help me with a problem I'm having. Currently I'm involved in a project at University to set up a wireless AP that's capable of broadcasting in the 760 MHz UHF area of the spectrum. In order to do this I need to be able to use 5 MHz channels. I was pointed towards the MadWiFi driver used by the dd-wrt firmware as a possible solutution (from [svn://svn.dd-wrt.com/DD-WRT](svn://svn.dd-wrt.com/DD-WRT))

However when I run sudo make I get this error

```
#./kernelversion.c:13: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
make: execvp: ./scripts/get_arch_target.sh: Permission denied
Makefile.inc:124: *** Cannot determine kernel architecture, please check /lib/modules/2.6.35-22-generic/build/.config. Stop.

```So far haven't been able to figure out what's wrong. 

System I'm running on is:

Ubuntu 10.10
old dell with Pentium 4
Ubiquiti XR7 radio


Any help would be massively appreciated!

---

