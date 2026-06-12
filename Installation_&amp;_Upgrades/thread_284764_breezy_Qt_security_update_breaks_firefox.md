---
title: "breezy: Qt security update breaks firefox"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Matt05 on 2006-10-26
Hi,

after doing the usual security update in kubuntu, firefox no longer works.  It freezes after a few seconds of use.  No error messages, no log entries are generated.  

The aptitude log of the security update:
```

Aptitude 0.2.15.9: log report
Thu Oct 26 08:35:55 2006


IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 6 packages, and remove 0 packages.
===============================================================================
[UPGRADE] libqt3-compat-headers 3:3.3.4-8ubuntu5 -> 3:3.3.4-8ubuntu5.1
[UPGRADE] libqt3-headers 3:3.3.4-8ubuntu5 -> 3:3.3.4-8ubuntu5.1
[UPGRADE] libqt3-mt 3:3.3.4-8ubuntu5 -> 3:3.3.4-8ubuntu5.1
[UPGRADE] libqt3-mt-dev 3:3.3.4-8ubuntu5 -> 3:3.3.4-8ubuntu5.1
[UPGRADE] qt3-designer 3:3.3.4-8ubuntu5 -> 3:3.3.4-8ubuntu5.1
[UPGRADE] qt3-dev-tools 3:3.3.4-8ubuntu5 -> 3:3.3.4-8ubuntu5.1
===============================================================================

Log complete.

```

Does anybody know how I can undo the security update?

Thanks,

  Matthias

---

### Post by Matt05 on 2006-10-26
Correction.  The security updates seem to be innocent.
After moving my ~/.mozilla to ~./mozilla.old firefox works as usual.
I've no idea what might have happened to the old configuration.

Matthias

---

