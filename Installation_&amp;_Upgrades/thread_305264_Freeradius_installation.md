---
title: "Freeradius installation"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by ubuntae on 2006-11-23
After i follow the Freeradius's manual, i get this error message.

root@ubuntu:~/Desktop/freeradius-1.1.3# ls
acconfig.h    configure     doc         ltconfig     missing  src
aclocal.m4    configure.in  INSTALL     ltmain.sh    raddb    suse
config.guess  COPYRIGHT     install-sh  Makefile     README   todo
config.h.in   CREDITS       libltdl     Make.inc.in  redhat
config.log    debian        libtool.m4  man          scripts
config.sub    dialup_admin  LICENSE     mibs         share
root@ubuntu:~/Desktop/freeradius-1.1.3# ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
root@ubuntu:~/Desktop/freeradius-1.1.3#

please advice.

---

### Post by ubuntae on 2006-11-23
I also try sudo apt-get install freeradius but got this message

root@ubuntu:~# sudo apt-get install freeradius
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package freeradius
root@ubuntu:~#

Why Ubuntu doesn't know Freeradius? Or I have another installation alternative for Freeradius on Ubuntu. I am a newbie and want to use Radius for WiFi security.

---

