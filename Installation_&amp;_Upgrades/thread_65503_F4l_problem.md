---
title: "F4l problem"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by Chxta on 2005-09-14
I downloaded f4l a program for creating flash animations in Linux, but installing has been real hell...

> 
dpkg: dependency problems prevent configuration of f4l:
f4l depends on libc6 (>= 2.3.2.ds1-21); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
f4l depends on libgcc1 (>= 1:4.0.0-9); however:
Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
Package libqt3c102-mt is not installed.
f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
Package libqt3c102-mt is not installed.
f4l depends on libfontconfig1 (>= 2.3.0); however:
Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
f4l depends on libxrender1 (>= 1:0.9.0-2); however:
Version of libxrender1 on system is 0.9.0-0ubuntu4.
f4l depends on libexpat1 (>= 1.95.8-3); however:
Version of libexpat1 on system is 1.95.8-1.
dpkg: error processing f4l (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
f4l

That's the message I've been getting, and I am not enjoying it. Help please.

---

### Post by buttabrick on 2007-10-11
if compiling is the issue try here:

[http://www.unfreeze.net/gpl/f4l/debian.php](http://www.unfreeze.net/gpl/f4l/debian.php)
check to make sure you have all the dependancies for kdevelop

or

[http://f4l.sourceforge.net/wiki/?title=Linux+Install](http://f4l.sourceforge.net/wiki/?title=Linux+Install)



this is the dependency list for f4l:
[http://rpmfind.net/linux/RPM/sourceforge/f/f4/f4l/F4L-0.2_BETA-1.i586.html](http://rpmfind.net/linux/RPM/sourceforge/f/f4/f4l/F4L-0.2_BETA-1.i586.html)


check here for definitive list of kdevelopment dependancies Note some packages listed as optional are needed for compiling f4l. 
[http://www.kdevelop.org/index.html?filename=3.4/requirements.html](http://www.kdevelop.org/index.html?filename=3.4/requirements.html)

:guitar:

---

