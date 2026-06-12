---
title: "Simple solution to linux-ubuntu-modules with a custom kernel?"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by beepbeepbeep on 2008-03-11
So I've switched to Ubuntu from Debian and I'm trying to do everything right.  Under Debian, I could download the Debianised source for a kernel module and it would get extracted to /usr/src/modules.  make-kpkg modules_image automagically compiled and packaged it whenever I recompiled my kernel.  It was beautiful!!  I see that this works on Ubuntu for some packages (e.g. fglrx-kernel-source), but the majority of useful modues are bundled up in linux-ubuntu-modules and linux-restricted-modules.  Is there any way to get the source to go in /usr/src/modules so that module-assistant and make-kpkg can work with it?  (I think fiesty did it this way.)  I've read various confused posts about recompiling the entire package, but I don't want or need the whole package!  Not only that, but the whole 'hack the deb scripts in the source directory to make it like your kernel' just adds so much more complexity to compiling a kernel!!

Any help would be greatly appreciated!  :-)

---

