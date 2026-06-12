---
title: "apt-get frequent segfaults"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HankB on 2010-04-14
```
hbarta@bonsai:~/bin$ dmesg|grep segfault
[  207.375272] apt-get[1455]: segfault at 0 ip 00514d10 sp bf8f6b4c error 4 in libc-2.11.1.so[434000+153000]
[  691.307796] apt-get[1580]: segfault at 0 ip 0020fd10 sp bfa6149c error 4 in libc-2.11.1.so[12f000+153000]
[10901.738584] apt-get[2447]: segfault at 0 ip 00229d10 sp bff0fa4c error 4 in libc-2.11.1.so[149000+153000]
[12889.757460] apt-get[3492]: segfault at 0 ip 00956d10 sp bf9d71cc error 4 in libc-2.11.1.so[876000+153000]
[13129.784692] apt-get[13480]: segfault at 0 ip 00efdd10 sp bf90ecac error 4 in libc-2.11.1.so[e1d000+153000]
[13180.704118] apt-get[17990]: segfault at 0 ip 001f0d10 sp bf9a1fbc error 4 in libc-2.11.1.so[110000+153000]
hbarta@bonsai:~/bin$
``` 

That really makes the hair crawl on the back of my neck. However, it seems not to have an affect on the system. I seem to be able to install, remove, update, upgrade w/out difficulty.

---

