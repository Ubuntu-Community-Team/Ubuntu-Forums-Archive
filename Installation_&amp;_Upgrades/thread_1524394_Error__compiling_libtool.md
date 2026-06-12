---
title: "Error  compiling libtool"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by CelticFiddle on 2010-07-05
Hi, 
 
I have been having this error while making libtool 2.2.8
 
```
 
make[2]: Entering directory `/home/emina/libtool-2.2.8'
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdl -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl/libltdl   -g -O2 -MT libltdl/loaders/libltdl_libltdl_la-preopen.lo -MD -MP -MF libltdl/loaders/.deps/libltdl_libltdl_la-preopen.Tpo -c -o libltdl/loaders/libltdl_libltdl_la-preopen.lo `test -f 'libltdl/loaders/preopen.c' || echo './'`libltdl/loaders/preopen.c
mv -f libltdl/loaders/.deps/libltdl_libltdl_la-preopen.Tpo libltdl/loaders/.deps/libltdl_libltdl_la-preopen.Plo
**mv: cannot stat `libltdl/loaders/.deps/libltdl_libltdl_la-preopen.Tpo': No such file or directory**
make[2]: *** [libltdl/loaders/libltdl_libltdl_la-preopen.lo] Error 1
 

```
 
Any clues?
 
( i can t use apt for [this reason]("http://ubuntuforums.org/showthread.php?p=9530376"))
 
Thanks alot for your help/ :D

---

