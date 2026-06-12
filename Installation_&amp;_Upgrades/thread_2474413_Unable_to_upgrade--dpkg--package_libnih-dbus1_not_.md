---
title: "Unable to upgrade--dpkg--package libnih-dbus1 not co-installable with libnih-dbus1?"
date: 2022-04-28
forum: Installation &amp; Upgrades
---

### Post by shansen5 on 2022-04-28
These two errors are preventing me from upgrading to 20.04.

dpkg: error processing archive /tmp/apt-dpkg-install-pWD8TX/07-libnih-dbus1_1.0.3-12_amd64.deb (--unpack):
 package libnih-dbus1:amd64 (1.0.3-12) with field 'Multi-Arch: no' is not co-installable with libnih-dbus1 which has multiple installed instances
dpkg: error processing archive /tmp/apt-dpkg-install-pWD8TX/08-libnih1_1.0.3-12_amd64.deb (--unpack):
 package libnih1:amd64 (1.0.3-12) with field 'Multi-Arch: no' is not co-installable with libnih1 which has multiple installed instances

Any hints appreciated!

---

### Post by gorthx on 2023-02-08
Hi!

You've probably already found an answer, but JIC someone else stumbles across this thread while trying to fix the same error: 

It's a known bug, and the fix is in the first comment:

[https://bugs.launchpad.net/ubuntu/+source/libnih/+bug/1948346](https://bugs.launchpad.net/ubuntu/+source/libnih/+bug/1948346)

gabrielle

---

