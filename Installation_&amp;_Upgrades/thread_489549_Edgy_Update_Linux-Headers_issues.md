---
title: "Edgy Update Linux-Headers issues"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by theak on 2007-07-01
On trying to update Edgy I get the following error, any suggestions on where to go from here

```
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a6.10+20070601_all.deb (--unpack):
 files list file for package `linux-headers-2.6.17-10' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a6.10+20070601_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by bapoumba on 2007-07-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please check this bug. There are refs to threads that can be helpful to you, or you can comment in the bug report.

---

### Post by theak on 2007-07-03
Thanks for your reply.  I took the easy way out and did a complete reinstall, all is now good.

---

