---
title: "Deb Package Versions: ubuntu versus build"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by blafrisch on 2008-02-21
Right now I'm working on a script to download the latest versions of all DEBs before repackaging the ISO and I have come across something that I'm unsure of:

In the Packages files many times there are two with very similar versions except one says "ubuntu" in it and one says "build".  Example:
[INDENT]pool/main/a/apache2/apache2-mpm-prefork_2.2.4-3ubuntu0.1_i386.deb
pool/main/a/apache2/apache2-mpm-prefork_2.2.4-3build1_i386.deb[/INDENT]


I can tell which is newer by looking online and seeing the date difference, but a date is not contained within the Packages file.  Can I assume that the one with "ubuntu" in the version is always newer?  Does it even matter?

Thanks,
- Mike

---

