---
title: "APT is completely confused... errors everywhere"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by doug-ravennasprings on 2014-02-19
When installing most anything, I get enormous errors that are themselves erroneous.

The dependencies of packages are flagged as problematic but reading the errors one can see the dependencies are met.

Ubuntu: 12.04.4 64 bit  [Stable?]

eg: Installing ClamTk
The following packages have unmet dependencies:

initscripts: Depends: debianutils (>= 4) but 4.4 is to be installed
             Depends: lsb-base (>= 3.2-14) but 4.1+Debian12 is to be installed
             Depends: coreutils (>= 5.93) but 8.21-1 is to be installed
netbase: 

Installation fails.


eg 2.0: Installing LibreOffice
The following packages have unmet dependencies:

initscripts: Depends: debianutils (>= 4) but 4.4 is to be installed
             Depends: lsb-base (>= 3.2-14) but 4.1+Debian12 is to be installed
             Depends: coreutils (>= 5.93) but 8.21-1 is to be installed
libreoffice: Depends: libreoffice-core (= 1:4.1.5-1) but 1:4.1.5-1 is to be installed
netbase: 

Everything seems to report similar errors.

---

### Post by ajgreeny on 2014-02-19
Show us the output of ```
sudo apt-get update
``` which may give some clues, and put the copied output in code tags, ie copy the output from terminal into the reply box by highlighting with mouse and right clicking ->copy; paste it the usual way, then select the whole of the copied text and click the # in the toolbar above.

I assume you have already run **sudo apt-get update**?

---

### Post by ian-weisser on 2014-02-19
[QUOTE=doug-ravennasprings;12933468]When installing most anything, I get enormous errors that are themselves erroneous.[QUOTE]

Well, not really.
The system is trying to tell you (poorly) that it is quite borked.

Example:
```
$ rmadison -u ubuntu debianutils
 debianutils | 3.2.2        | lucid   | source, amd64, armel, i386, ia64, powerpc, sparc
 debianutils | 4.2.1ubuntu2 | precise | source, amd64, armel, armhf, i386, powerpc
 debianutils | 4.3.4        | quantal | source, amd64, armel, armhf, i386, powerpc
 debianutils | 4.4          | saucy   | source, amd64, arm64, armhf, i386, powerpc
 debianutils | 4.4          | trusty  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

If you were running 12.04, the version of debianutils should be 4.2.1ubuntu2.
But you're running 4.4, the version for 13.10 or 14.04.

So either you are running a newer version of Ubuntu than you think, or you have added quite inappropriate repositories to update from. The latter will break your system in very much the way you describe. If unlucky, the latter can also make your system unstable or unbootable.

---

