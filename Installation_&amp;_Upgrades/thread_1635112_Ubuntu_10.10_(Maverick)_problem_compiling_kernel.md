---
title: "Ubuntu 10.10 (Maverick) problem compiling kernel"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by FA-MAS on 2010-12-01
Got the kernel thing sorted.  Please check my latest post for new issue.

Hi, I'm running ubuntu 10.10 (Maverick) and Update Manager ran so I'm running the newest Kernel available 2.6.35-23-generic. I'm trying to compile my Kernel to add a couple modules and I'm getting an error when I run "make-kpkg clean". 
 
I'm using the guide here: [http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)
 
Looks like it's from 2006, I haven't used ubuntu in a while so I'm guessing the process has changed or I'm doing something wrong.  Here is the error I get, I was wondering if someone could help me. Any help is appreciated.
 
root@AOD255:/usr/src/linux# make-kpkg clean
exec make kpkg_version=12.033 -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
This is kernel package version 12.033.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
make ARCH=i386 distclean
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
/usr/src/linux-headers-2.6.35-23-generic/ubuntu/aufs/Makefile:3: ubuntu/aufs/magic.mk: No such file or directory
make[3]: *** No rule to make target `ubuntu/aufs/magic.mk'. Stop.
make[2]: *** [ubuntu/aufs] Error 2
make[1]: *** [_clean_ubuntu] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [minimal_clean] Error 2

---

### Post by FA-MAS on 2010-12-01
Looking at the error further, it kinda looks like it's trying to make aufs and that's where it's failing.  Anyone have any ideas?

---

### Post by FA-MAS on 2010-12-02
Got the kernel thing sorted.

I later ran:
su root nautilus

So I could copy a file (quake3's pk3 file) into a directory via gui and instead of bring up nautilus as root, it said "user added" and I don't know what it did.  Anyone have any ideas?

---

