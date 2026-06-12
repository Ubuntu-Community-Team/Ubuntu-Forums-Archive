---
title: "Upgrade to 21.04 from 20.10"
date: 2021-06-01
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2021-06-01
I don't get the automatic suggestion to upgrade from 20.10 to 21.04.  I was a little late upgrading to 20.10, just completing it about a week ago or so.

I've changed the settings from LTS release to any release, and back and forth with no suggestion.

I've tried the force upgrade via terminal with the -c and -d, but was offered a development release I believe.  I didn't want that.

How do I upgrade to the stable release?

D

---

### Post by Dennis N on 2021-06-01
Did you fully update your system? Otherwise, Software Updater will not offer an upgrade.
Also see this thread, posts #7 and #8 for methods + accounts of successful upgrades:
[https://ubuntuforums.org/showthread.php?t=2462611](https://ubuntuforums.org/showthread.php?t=2462611)

---

### Post by guiverc on 2021-06-01
I wrote an answer here on the issue - [https://askubuntu.com/questions/1338429/ubuntu-21-04-update-available-then-disappears/1338851#1338851](https://askubuntu.com/questions/1338429/ubuntu-21-04-update-available-then-disappears/1338851#1338851)

The Ubuntu 21.04 release notes stated the upgrade path was **not **open 

> Upgrades from Ubuntu 20.10 to Ubuntu 21.04 are not enabled as it is possible for some systems to end up in an unbootable state if they use EFI version 1.10 - bug 1925010. Release upgrades will be enabled once an updated version of shim is available which is compatible with EFI version 1.10.

That original SHIM issue has been resolved, thus the upgrade was briefly opened... However another SHIM issue was discovered (*meaning boxes that upgraded would not boot post-upgrade*) and thus the upgrade path was closed again.

I provide my 2c. in that post, ie.

> It's again SHIM issues impacting other [versions & makes]("https://bugs.launchpad.net/bugs/1928434")...  though that's just one issue being watched & part of the decision.   This answer is based on discussions in #ubuntu-release in IRC

The file that determines what upgrades are available to you (with & without the `-d` flag) I discuss in the askubu question I've linked to, but key file is [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) which does **not** list 21.04, thus a 20.10 system **will not see the upgrade yet** (*without `-d` to force it as that uses a different file*)

---

