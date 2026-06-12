---
title: "Installing madwifi drivers on Unbuntu 10"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by ArjsDk on 2010-11-16
I try using some tips from here on how to install madwifi drivers...The tip where for  ubuntu 8.0 and im using ver. 10, but it should be the same way I install...

Im pretty new to linux, but i keep getting this error message when i try to make the drivers:


[COLOR=Black]menace@meance:~/madwifi-0.9.4$ make clean[/COLOR]

[COLOR=Red]./kernelversion.c:13: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH. Stop.[/COLOR]

Can anyone help me with what to do??

---

### Post by cybergnome on 2010-11-16
Ubuntu 8.xx had what is now referred to as the "old madwifi", which used atheros hal.  The new ath5k is included in Ubuntu 10.xx, and works for me without any special tools for configuration.  The basic Linux networking tools are sufficient.

You probably don't need the "old madwifi", but if you do, you need to remove the new one prior to installing.

---

