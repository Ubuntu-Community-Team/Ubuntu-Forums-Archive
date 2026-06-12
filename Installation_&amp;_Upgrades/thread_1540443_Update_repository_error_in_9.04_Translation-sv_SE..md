---
title: "Update repository error in 9.04: Translation-sv_SE.bz2 not found"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Thomasikus on 2010-07-27
Hi!
Running Ubuntu 9.04, Swedish language variant. When in Update Manager I click the "Check" button, the indexes reload, but at the end an error message is displayed:

[I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
[http://se.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-sv_SE.bz2](http://se.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-sv_SE.bz2)
[http://se.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://se.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)
[http://se.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-sv_SE.bz2](http://se.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-sv_SE.bz2)
[http://se.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-sv_SE.bz2](http://se.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-sv_SE.bz2)
[http://se.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-sv_SE.bz2](http://se.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-sv_SE.bz2)
[http://se.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-sv_SE.bz2](http://se.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-sv_SE.bz2)
[http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-sv_SE.bz2](http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-sv_SE.bz2)
[/I]
In all cases, Update Manager states that the index could not be retrieved because the other end closed the connection. Manually checking these locations (with Firefox) show that there is no file called "Translation-sv_SE.bz2", but a file called "Translation-sv.bz2" does exist.
The file "Release.gpg" may have something to do with Medibuntu; I'm not sure.

How can I correct this problem?

---

