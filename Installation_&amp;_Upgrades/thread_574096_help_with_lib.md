---
title: "help with lib"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by abcquirk on 2007-10-12
Hi

I'm using Ubuntu 7.04 as devlopment sys for debugging and compilation. The app I wrote is intended to run on an embeded linux (kernel 2.4.20) which has an earlier library version than the one on Ubuntu. I must not have a newer version of library on my dev sys, orelse I'm getting error messages. So can anyone tell me HOW to **downgrade** the library on Ubuntu? 

GLIBC version: 2.2

gcc version 2.95.4

here is what I found in /lib directory on the embeded linux

drwxr-xr-x 3 root root 608 Apr 1 2004 .
drwxr-xr-x 15 root root 480 Apr 1 2004 ..
-rwxr-xr-x 1 root root 74252 Apr 1 2004 ld-2.2.5.so
lrwxrwxrwx 1 root root 11 Apr 1 2004 ld-linux.so.2 -> ld-2.2.
5.so
-rwxr-xr-x 1 root root 1203560 Apr 1 2004 libc-2.2.5.so
lrwxrwxrwx 1 root root 13 Apr 1 2004 libc.so.6 -> libc-2.2.5.
so
-rwxr-xr-x 1 root root 20712 Apr 1 2004 libcrypt-2.2.5.so
lrwxrwxrwx 1 root root 17 Apr 1 2004 libcrypt.so.1 -> libcryp
t-2.2.5.so
lrwxrwxrwx 1 root root 17 Apr 1 2004 libncurses.so.5 -> libnc
urses.so.5.0
-rwxr-xr-x 1 root root 289484 Apr 1 2004 libncurses.so.5.0
-rwxr-xr-x 1 root root 12548 Apr 1 2004 libnss_dns-2.2.5.so
lrwxrwxrwx 1 root root 19 Apr 1 2004 libnss_dns.so.2 -> libns
s_dns-2.2.5.so
-rwxr-xr-x 1 root root 34932 Apr 1 2004 libnss_files-2.2.5.so
lrwxrwxrwx 1 root root 21 Apr 1 2004 libnss_files.so.2 -> lib
nss_files-2.2.5.so
-rwxr-xr-x 1 root root 55380 Apr 1 2004 libresolv-2.2.5.so
lrwxrwxrwx 1 root root 18 Apr 1 2004 libresolv.so.2 -> libres
olv-2.2.5.so
-rwxr-xr-x 1 root root 8424 Apr 1 2004 libutil-2.2.5.so
lrwxrwxrwx 1 root root 16 Apr 1 2004 libutil.so.1 -> libutil-
2.2.5.so
drwxr-xr-x 2 root root 448 Apr 1 2004 modules

Thank you

---

