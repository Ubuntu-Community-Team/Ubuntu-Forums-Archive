---
title: "VirtualBox client additions broken by upgrade to 13.10"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by bkline on 2013-11-03
The 13.10 release of Ubuntu is turning out to be an unlucky number, as several things are broken by the upgrade to it.  The latest is that the shared folders I had between a VirtualBox client and the host stopped working as soon as I upgraded to 13.10.  Things were working perfectly before the upgrade, and now the `ls` command either hangs or returns with an out of memory error when used to list the contents of one of the shared folders.  Anyone else experience this problem?  Unfortunately, I can't tell whether it was the upgrade of the host or the guest which caused the problem, as I upgraded both at the same time.

---

### Post by pqwoerituytrueiwoq on 2013-11-03
just reinstall/update the guest addons on the virtual machine
not having any issues with the ls command here and i upgraded from 13.04 to 13.10
using xubuntu

---

### Post by bkline on 2013-11-09
I tried reinstalling the guest addons, but didn't have any success.  It turns out that this is a documented bug:

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1239384](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1239384)

---

