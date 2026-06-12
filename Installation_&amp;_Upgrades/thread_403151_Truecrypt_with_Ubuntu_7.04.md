---
title: "Truecrypt with Ubuntu 7.04"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by inorrish on 2007-04-06
Just upgraded to 7.04 from 6.10 but find I can't open Truecrypt volumes produced under 6.10.
Is there a fix?

---

### Post by anthro398 on 2007-04-07
It works for me.  I had to reinstall Truecrypt by compiling from source.  Also, the /usr/src/linux symlink was point to 2.6.17 instead of 2.6.20 so I had to bunzip2 and untar the source for the 2.6.20 kernel, destroy the old symlink and create a new one.  Works fine.

---

