---
title: "package help"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by saintpa on 2005-05-25
I installed an unstable version of libc6 to get one of my apps to work. But now whenever I do dist-upgrade, apt-get reports a dependency conflict:

The following packages have unmet dependencies:
libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is installed
libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is installed
locales: Depends: glibc-2.3.2.ds1-20ubuntu13
E: Unmet dependencies. Try using -f.

How can I revert libc6 to ubuntu version to resolve this conflict? Any help would be appreciated.

---

### Post by Xian on 2005-05-25
Duplicate [THREAD](http://www.ubuntuforums.org/showthread.php?t=37115).

---

