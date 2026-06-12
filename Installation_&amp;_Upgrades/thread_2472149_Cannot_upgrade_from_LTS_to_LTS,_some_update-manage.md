---
title: "Cannot upgrade from LTS to LTS, some update-manager error"
date: 2022-02-18
forum: Installation &amp; Upgrades
---

### Post by kierprev on 2022-02-18
I'm trying to do do-release-upgrade -d to upgrade to the development version of 22.04 LTS.

But the installation aborts.

My [main log]("https://pastebin.com/nmVMu0D0"), and my [apt.log]("https://pastebin.com/pJrKbVDF")

---

### Post by guiverc on 2022-02-18
I've [already provided clues]("https://askubuntu.com/questions/1393703/cannot-upgrade-from-lts-to-lts-some-update-manager-error").

You're using OIBAF graphics drivers; which prevent `[ubuntu-release-upgrader]("https://launchpad.net/ubuntu/+source/ubuntu-release-upgrader")` from running.

Those need to be purged first.

If you read [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) I'd provided you'll have noted that.  It tells you

> === Upgrading to a newer Ubuntu ===
It is *strongly* suggested to remove all packages from this PPA before  updating to a newer Ubuntu release. See the section "Revert to original  drivers" later on.
Then, after the upgrade, you can add again this PPA.

If you file a bug report, it'll be marked a duplicate of [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1069133](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1069133)

I didn't scan the total of your logs, but stopped when I saw a ***blocker ***issue which is the use of OIBAF graphics drivers.

---

