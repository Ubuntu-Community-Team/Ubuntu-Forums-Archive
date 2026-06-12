---
title: "lib64 in 32-bit Ubuntu"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by adityagadre on 2010-09-29
I recently installed 32-bit ubuntu 10.04.1 LTS. Looking at the directory structure, I found /usr/lib64. This comes as a surprise to me since the installation is a 32-bit install. Is this normal? Thanks.

---

### Post by oldos2er on 2010-09-29
Can you run **uname -a** in a terminal, and post the output here?

---

### Post by adityagadre on 2010-09-29
Here is the output of "uname -a"

Linux riverinedev 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux

---

### Post by oldos2er on 2010-09-30
That would confirm you're running 32-bit (i686). Maybe someone else with a 32-bit install can comment on the existence of a /usr/lib64 folder. Just out of curiosity, is there anything in that folder?

---

### Post by adityagadre on 2010-09-30
Thanks for your replies.

In the directory structure, I have the following directories.

/usr/lib
/usr/lib32
/usr/lib64

Note that /usr/lib is not a link to any of the other two directories.

/usr/lib has all the libraries I have installed using aptitude.

/usr/lib32 has two library directories - nvidia-current and vdpau - both of which are empty.

/usr/lib64 has one library directory - libfakeroot - which contains two shared libraries (libfakeroot-sysv.so  libfakeroot-tcp.so).

---

