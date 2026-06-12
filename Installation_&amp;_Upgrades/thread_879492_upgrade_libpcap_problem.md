---
title: "upgrade libpcap problem"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by scuba123 on 2008-08-04
Hi Everybody,

I downloaded libpcap0.9.8 for upgrades from this link -> [https://launchpad.net/ubuntu/intrepid/+source/libpcap/0.9.8-5](https://launchpad.net/ubuntu/intrepid/+source/libpcap/0.9.8-5). I then ran the command as follows:
1. ./configure
2. sudo make install
My question is that I couldn't find **/usr/lib/libpcap.so.0.9.8**. I only found:
-rw-r--r-- 1 root root 147048 2004-08-12 19:33 /usr/lib/libpcap.a
lrwxrwxrwx 1 root root     14 2008-08-04 00:00 /usr/lib/libpcap.so -> libpcap.so.0.7
lrwxrwxrwx 1 root root     16 2008-07-12 16:46 /usr/lib/libpcap.so.0.7 -> libpcap.so.0.7.2
-rw-r--r-- 1 root root 117136 2004-08-12 19:33 /usr/lib/libpcap.so.0.7.2
lrwxrwxrwx 1 root root     16 2006-12-27 03:15 /usr/lib/libpcap.so.0.8 -> libpcap.so.0.9.4
-rw-r--r-- 1 root root 155152 2006-06-19 12:41 /usr/lib/libpcap.so.0.9.4

Do you have any ideas? Please help. Thanks in advance.

Regards,

scuba123

---

### Post by Sef on 2008-08-04
Locked. [Duplicate Post]("http://ubuntuforums.org/showthread.php?t=879494").

---

