---
title: "Size limit for .deb packages?"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by moto_tux on 2012-05-14
We have had problems with custom packages which are over 2Gb in size.  Has anyone else encountered this or know of fixes or work arounds?

The errors we get are "Size mismatch" or "bad magic at end of first header" when in repo or installing manually with dpkg -i respectively.

It seems to be an underlying issue with dpkg (possibly using signed integer rather than unsigned and/or long data type somewhere.  However I can't find many references to this, one workaround is to use a different compression which helps if the package isn't too much bigger, ie:
dpkg-deb -Zlzma -b <folder> <deb package name>
(from [http://sshrootat.blogspot.co.uk/2011/10/2gb-deb-package-limit.html]("http://sshrootat.blogspot.co.uk/2011/10/2gb-deb-package-limit.html"))

I also can't find a bug which actually covers this problem (although this may be because I'm not sure where to look!)

Any thoughts or help would be great please.

We're using Lucid 10.04.4
dpkg version 1.15.5.6ubuntu4.5

---

