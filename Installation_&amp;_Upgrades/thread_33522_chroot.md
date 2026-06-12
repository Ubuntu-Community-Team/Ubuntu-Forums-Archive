---
title: "chroot"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2005-05-11
hi , i installed, or tried to install chroot, finished it, but when i try to login:
aaaaa@pirat:/chroot$ ssh localhost -l test
Password:
Linux pirat 2.6.11.7 #1 Sun May 8 12:20:21 WST 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed May 11 20:33:57 2005 from localhost.localdomain
-bash: /lib/ld-linux.so.2: version `GLIBC_PRIVATE' not found (required by /lib/tls/libdl.so.2)
-bash: /lib/ld-linux.so.2: version `GLIBC_2.3' not found (required by /lib/tls/libc.so.6)
-bash: /lib/ld-linux.so.2: version `GLIBC_PRIVATE' not found (required by /lib/tls/libc.so.6)
Connection to localhost closed.



what did i do wrong? what did i miss ? :)

also i couldn't find any how-to on google etc. just one usefull,
please advise. 
thanks

---

### Post by JonahRowley on 2005-05-11
When setting up a chroot environment, you must have ALL dynamic libraries needed to run whatever software you're running.  To simplify things, you can do static builds instead.  apt-build might help you there, somehow.

---

### Post by [pl]ice on 2005-05-12
thnx

are there any HOW-TO for debian /ubuntu?

the HOW-TO used static but which actual lib. this error refers to? i though it was Glibc , am i correct?

thanks

---

