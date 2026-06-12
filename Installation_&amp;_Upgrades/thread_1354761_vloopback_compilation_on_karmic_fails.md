---
title: "vloopback compilation on karmic fails"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by surfer63 on 2009-12-14
Hi,

I try to compile the vloopback-source on Karmic.
I first downloaded the vloopback-source package for karmic, but compilation failed as that version was 1.1-1 and is too old for the 2.6.31 kernel which karmic has.
Then I downloaded the vloopback 1.3 source which should be compatible with 2.6.31, but compilation failed again.
Then I downloaded the svn version (svn co [http://www.lavrsen.dk/svn/vloopback/trunk/](http://www.lavrsen.dk/svn/vloopback/trunk/) vloopback), but all give the same error upon compilation:
```
make -C /lib/modules/2.6.31-16-generic-pae/build SUBDIRS=/opt/software/vloopback modules
make[1]: Entering directory `/lib/modules/2.6.31-16-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.31-16-generic-pae/build'
make: *** [all] Error 2
```

Then I tried to install the modules source with "apt-get source linux-ubuntu-modules-$(uname -r)". That one does not exist. With more generic approaches (for my kernel 2.6.31-16-generic-pae) like "linux-ubuntu-modules-2.6.31-16-generic" or linux-ubuntu-modules-2.6.31-16""  or "linux-ubuntu-modules" I had no success in downloading either.

Note: I noticed that [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) mentions that this doesn't function for 9.10.

Please tell me what I have to do work around this and to get vloopback compiled.

---

