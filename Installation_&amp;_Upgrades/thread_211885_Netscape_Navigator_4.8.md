---
title: "Netscape Navigator 4.8"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by steven_ellis on 2006-07-09
Now I know this might seem a little odd but I have a couple of legacy applications that prefer netscape 4.x over any of the more recent browsers. Under Hoary Breezy I had used alien to convert the Dag Wiers FC2 netscape-navigator and netscape-common 4.8 packages into deb files. This worked perfectly.

Since upgrading to Dapper I can't use my old packages. The will start but crash after only a couple of minutes. If I attempt to strace it I just get the following

```
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b31000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
getpid()                                = 13196
kill(13196, SIGBUS)                     = 0
--- SIGBUS (Bus error) @ 0 (0) ---
+++ killed by SIGBUS +++

```

Anyone else tried to run any legacy libc5 packages under Dapper? Any ideas what I can do as a work around here as I really need this package.

Steve

---

