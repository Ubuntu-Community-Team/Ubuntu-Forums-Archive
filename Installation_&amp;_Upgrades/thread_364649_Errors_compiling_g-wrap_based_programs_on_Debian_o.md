---
title: "Errors compiling g-wrap based programs on Debian or Ubuntu"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Greg Clark on 2007-02-18
Can someone** interpret** the last bit for me please.. which file am I editing and where will I find it ?

Thanks 

Greg 

Errors compiling g-wrap based programs on Debian or Ubuntu

If you get errors due to <g-wrap-wct.h> being missing, this is due to this file being incorrectly dropped from the Debian package of g-wrap (and the mistake copied in Ubuntu's universe repository). The file is in fact trivial, because it's only there as a compatibility bridge for old programs that have not updated to use the newer header:

/* Provided for compatibility with G-Wrap 1.3.4 */

#include <g-wrap/guile-wct.h>

So you could just edit the offending file to use the new header. I didn't realise this until I had done the long-winded solution: adding /usr/include/g-wrap-wct.h to debian/guile-g-wrap.install and rebuilding the Debian package.

---

