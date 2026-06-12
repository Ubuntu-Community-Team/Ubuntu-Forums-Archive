---
title: "Scons error while installing LinuxDC++"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by Codename46 on 2007-10-14
Hey guys,

I'm trying to install LinuxDC++. However, upon typing " scons release=1 PREFIX=/usr/local" I get the following error:

scons: *** Error writing options to file: build/sconf/scache.conf
[Errno 2] No such file or directory: 'build/sconf/scache.conf'
File "/home/codename46/linuxdcpp/SConstruct", line 68, in <module>

I really want to get LinuxDC++ working. Does anyone know why Scons is doing this?

Thanks.

---

### Post by Codename46 on 2007-10-14
bump?

Anyone? =(
I am using this guide BTW:

[http://ubuntuforums.org/showthread.php?t=193984](http://ubuntuforums.org/showthread.php?t=193984)

---

### Post by 3rods on 2007-10-14
Make both of those directories, build and sconf (./build/sconf/) and create an empty scache.sconf file with vim or your favorite text editor. 

At they very least, it will start to build.

---

