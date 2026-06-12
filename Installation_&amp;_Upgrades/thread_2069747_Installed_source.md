---
title: "Installed source"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by h66m9d on 2012-10-11
where is installed software that installed from source code?
for example:
when I'm installing samba from source file:
1-extract it on "/home/USERNAME/source"
2-"./configure"
3-"make"
4-"make install"


Question:can I delete "/home/USERNAME/source"?
Question: where was installed samba?

---

### Post by spjackson on 2012-10-11
In the general case, if you don't specify another location to configure, then the software will be installed in /usr/local/..., e.g. /usr/local/bin, /usr/local/doc, /usr/local/share/... etc.

I can't be certain that this is true of the Samba source, but I very much expect so.

Yes, the source tree you used for building can be removed once the software is installed and working.

---

