---
title: "Upgraded to 11.04 but Canon Mp495 won't work"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by theetommyt on 2011-04-05
Just upgraded to a clean install from 10.04 to 11.04 and my Canon MP495 Printer drivers will not install. I get the "Package is of Bad Quality" (not the first package that has said this in 11.04) with these details:



Lintian check results for /home/tommyt/cnijfilter-common_3.40-1_i386.deb:
W: cnijfilter-common: copyright-without-copyright-notice
W: cnijfilter-common: binary-without-manpage usr/bin/cngpij
W: cnijfilter-common: binary-without-manpage usr/bin/cnijnetprn
W: cnijfilter-common: binary-without-manpage usr/bin/cnijnpr
W: cnijfilter-common: command-with-path-in-maintainer-script postrm:4 /sbin/ldconfig
W: cnijfilter-common: maintainer-script-ignores-errors postrm
W: cnijfilter-common: command-with-path-in-maintainer-script postinst:4 /sbin/ldconfig
W: cnijfilter-common: maintainer-script-ignores-errors postinst
W: cnijfilter-common: new-package-should-close-itp-bug
E: cnijfilter-common: ldconfig-symlink-missing-for-shlib usr/lib/libcnnet.so usr/lib/libcnnet.so.1.2.0 libcnnet.so
W: cnijfilter-common: shlib-without-versioned-soname usr/lib/libcnnet.so.1.2.0 libcnnet.so
W: cnijfilter-common: postrm-unsafe-ldconfig
W: cnijfilter-common: package-name-doesnt-match-sonames libcnnet


Is there a fix?

---

### Post by Linux_junkie on 2011-04-05
11.04 is still at beta (testing) stage you should not have installed this version unless you are planning on testing it and reporting bugs.

---

### Post by mörgæs on 2011-04-05
Hi, welcome to the fora.

It would be a great help, if you could report this kind of bugs in Launchpad:
[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)

---

### Post by modsbyus on 2011-05-12
Locate the ppd files associated with the drivers you have installed and (add) a new printer and choose to import a postscript file to install the printer.

---

