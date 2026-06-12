---
title: "Bulding .deb Packages for php-code"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by Cyber1000 on 2011-01-02
Hi all!
I'm starting with my first .deb packages ...
I've found information about debian-packages, how to build simple packages, ... .
So far so good.

But I've still a question which I can't find an answer for:
I have some php-code I want to package (mediawiki-extensions), I wanted to use dh_make, but dh_make and the later use of dpkg-buildpackage expects source and (afterwards) compiled binaries.

Is there a command which prepares the directory like dh_make and dpkg-buildpackage, but not for source-compilation, but for my php-files?

---

