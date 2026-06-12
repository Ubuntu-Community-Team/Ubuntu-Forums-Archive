---
title: "corrupt package db after failed 8.04 upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by shcodip on 2008-04-26
So during the upgrade of 7.10 I received multiple package errors.. things like.. 'files list for package 'gimp-data' contains empty filename'

The upgrade continued but in the end haulted and attempted to backup. During the process though the package db became corrupt and now I can't use apt-get or dpkg at all without getting errors like..

dpkg-query: files list file for package 'gimp-data' contains empty filename

Anyone know how to fix the package DB so I can attempt the upgrade again.

---

