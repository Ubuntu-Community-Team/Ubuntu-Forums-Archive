---
title: "tar.gz file install"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Juvencio on 2011-01-12
Is it Possible to install tar.gz files in ubuntu 64bit 10.4?

---

### Post by davidmohammed on 2011-01-12
yes - you need to gunzip the file and then untar the file.  Then you would compile the software.  The method to compile is generally running ./configure, followed by make  and finally a sudo make install.  

However - you should first search in software centre/google to see if there is a deb package for your software.  Its easier to install.

what is the tar.gz file?

---

