---
title: "dist-upgrade problem"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by jolosan on 2008-01-29
Hello, I'm using Ubuntu Feisty.
When I try to do any packet installation or an upgrade, dpkg returns the folowing error:
***************************************
dpkg: error when processing 
/var/cache/apt/archives/perl-modules_5.8.8-7ubuntu0.1_all.deb (--unpack):
the file of the list of files of the packet `language-pack-kde-es-base' contains an empty file name
Errors where found when processing:
 /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu0.1_all.deb
Halted process for too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
*****************************************

I've tryed to do "apt-get -f install"  and "dpkg --force-all -i perl-modules_5.8.8-7ubuntu0.1_all.deb" but it doesn't work.

Any help?

Thank you.

---

### Post by dabang on 2008-01-30
Not quite sure what happened, maybe a corrupted download? To get rid of (all!) the files in apt's cache type
```
sudo apt-get clean
```

Then try again...

---

### Post by jolosan on 2008-01-30
Hi, I've tried this, but after downloading again 120Mb in files, the problem is exactly the same.

---

