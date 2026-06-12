---
title: "maya-newbie"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by TripleDDesigner on 2005-09-07
I really need some help, and i know this is a stupid question.

when I try to convert the Maya .rpm packages to .deb alien instead extracts each one into a group of folders.  And when I try to find a the .deb file for the package i can'tfind any to install.  
This is a really stupid problem and I am probibly doing something wrong but I am stumped.

I've tried 
alien 
alien -d  
etc.

---

### Post by srinath on 2005-09-08
I am a newbie too. Sorry, I can't help but which maya are you talking about?

---

### Post by TripleDDesigner on 2005-09-08
is a copy of maya 7.0 

when I try to run alien it returns this log
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/maya7-0
dh_compress
dh_makeshlibs
dh_installdeb
install: cannot create directory `debian/maya7-0/DEBIAN': File exists
dh_installdeb: command returned error code 256
make: *** [binary-arch] Error 1
        find Maya7_0-7.0 -type d -exec chmod 755 {} ;
find: Maya7_0-7.0: No such file or directory
        rm -rf Maya7_0-7.0

---

### Post by johannes on 2005-09-09
Have you tried to follow the advices in [http://www.ubuntuforums.org/showthread.php?t=45748&highlight=maya](http://www.ubuntuforums.org/showthread.php?t=45748&highlight=maya)?
It's for Maya 6.5 but some things might work.

---

