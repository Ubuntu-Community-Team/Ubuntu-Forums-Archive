---
title: "nessus results"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by cabala on 2007-09-17
after install and full set of updates, nessus reports several updates being needed:

gimp, krb53, iceweasel, GPG, samba etc...

BUT - the "automatic"update manager cannot supply them  and says the system is up to date.

one may simply be a misread of the package name (GIMP) but krb53 is definitely an older version... 1.4.4-5 instead of -7     CVE-2007-3999

How/when can the updated packages for "feisty" be made available? Other solution?

---

### Post by dixonp on 2007-09-17
It could be a nessus false positive. To make sure you are really up-to-date, run:

  $ sudo apt-get update
  $ sudo apt-get upgrade

(or the equivalent operation with whatevere graphical APT frontend you are familiar with). Also, show us the content of /etc/apt/sources.list to make sure you didn't (inadvertently) mess up with it :)

---

