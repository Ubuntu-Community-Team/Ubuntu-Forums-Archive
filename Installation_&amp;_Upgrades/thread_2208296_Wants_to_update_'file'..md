---
title: "Wants to update 'file'."
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by Je Et on 2014-02-27
Received this update and I have never saw an update called 'file'. What is it?

---

### Post by howefield on 2014-02-27
[http://packages.ubuntu.com/precise/file](http://packages.ubuntu.com/precise/file)

---

### Post by slickymaster on 2014-02-27
File tests each argument in an attempt to classify it. There are three sets of tests, performed in this order: filesystem tests, magic number tests, and language tests. The first test that succeeds causes the file type to be printed.

Starting with version 4, the file command is not much more than a wrapper around the "magic" library.

[Package: file (5.11-2ubuntu4.1)]("http://“file” package in Ubuntu")

---

### Post by Dennis N on 2014-02-27
Put the name of a file after it (with path if not in the working directory) and it tells you what kind of file it is:

```
dmn@Zotac:~$ file todaysnews 
todaysnews: data
dmn@Zotac:~$ file Passwords.txt 
Passwords.txt: ASCII text
dmn@Zotac:~$ file keepassx.kdb 
keepassx.kdb: DBase 3 data file
dmn@Zotac:~$ file Videos
Videos: directory
dmn@Zotac:~$ file /usr/bin/file
/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xe0059552c9447cdef6331b833b26f5ddc3810229, stripped


```

---

