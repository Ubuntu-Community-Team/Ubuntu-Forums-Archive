---
title: "Ubiquity.components.partman failed - Exit Code 10"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by iClouseau88 on 2010-04-11
Hi,

I am re-installing Ubuntu onto my desktop PC which has Windows 7, openSUSE 11.2 and Fedora Core 12. First I tried Ubuntu 9.10.  Near the end of the installation the machine reboots and the monitor shows the following message:

"**Ubiquity.components.partman failed - Exit code 10.  Further info in /var/log/syslog**"

Tried again with Ubuntu 10.04 beta2 with same problem.

How can I view and read /var/log/syslog if Ubuntu fails to be installed and therefore I cannot access this log?

I would appreciate your help and practical solutions.

:(

---

### Post by iClouseau88 on 2010-04-13
Hello everyone,

Problem solved. I went into BIOS and changed the default PNP=NO (because XP takes care of this) to PNP= YES.

---

