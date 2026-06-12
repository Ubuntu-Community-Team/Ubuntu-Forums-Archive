---
title: "Chillispot dependency issues"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by bmquintas on 2005-10-09
Hi all, i'm trying to set up chillispot in a ubuntu box, but i'm getting this error:

chillispot depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.

Can somebody give a tip to correct this?

---

### Post by sjpwong on 2006-02-14
You will probably need to compile from source yourself or upgrade to Breezy (I'm guessing you are using Hoary).

The best bet is probably to compile yourself in this case as the packages on the website are Debian packages that may not be configured correctly for Ubuntu.

YMMV

P.S. I'll be compiling from source.

---

