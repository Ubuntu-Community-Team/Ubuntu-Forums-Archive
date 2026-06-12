---
title: "[SOLVED] Removing self-built packages deletes directories"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by keithweddell on 2008-10-05
I've been learning how to build ubuntu deb files using dh_make and debuild and have got to the point where I can install my programs.  But when I try to remove them using dpkg --remove <package> or dpkg --purge <package>, I find that dpkg is trying to remove system directories (e.g. /usr/local).  I have presumably made some mistake in configuring and building the deb file.  Any pointers to where the mistake may be?


Ketih

---

### Post by keithweddell on 2008-10-06
OK.  This seems to have happened because I was installing into non-standard directories (ie /usr/local...).  I modified the package to install into /usr/bin and /usr/share and it now installs and removes cleanly.

Keith

---

