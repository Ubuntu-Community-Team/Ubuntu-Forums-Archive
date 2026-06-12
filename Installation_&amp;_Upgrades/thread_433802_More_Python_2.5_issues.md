---
title: "More Python 2.5 issues"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by taddy_porter on 2007-05-05
I've found several threads on people with the Python2.5 issues. I've tried all the solutions I've found, but none work for me.

I initially had 4 broken packages I had to fix manually. No big deal, but the Python2.5 is not allowing me to upgrade other packages. I get errors about having the 2.4 installed, even though I've had 2.5 for some time. I tried to reinstall manually but get the following:

Preparing to replace python2.5-minimal 2.5.1~rc1-0ubuntu3 (using python2.5-minimal_2.5.1~rc1-0ubuntu3_i386.deb) ...
Unpacking replacement python2.5-minimal ...
Setting up python2.5-minimal (2.5.1~rc1-0ubuntu3) ...
Linking and byte-compiling packages for runtime python2.5...
usage: pycentral [<options> ...] rtinstall <options>

pycentral: error: no such option: --ignore-errors
dpkg: error processing python2.5-minimal (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.5-minimal


I tried commenting out lines 540 & 541 in the python file as suggested on another thread, but no luck. Any ideas on what to do next? Aptitude won't work either.

---

