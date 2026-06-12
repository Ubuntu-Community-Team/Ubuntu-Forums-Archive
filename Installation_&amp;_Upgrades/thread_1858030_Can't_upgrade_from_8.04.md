---
title: "Can't upgrade from 8.04"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by saenger on 2011-10-11
On my Dell Mini, I have 8.04 installed.  I have been unable to upgrade to a newer version.

When I try to upgrade, I get this:

wes@wes:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

I've tried both "prompt=normal"
and
"prompt=lts"
in the release-upgrades file.

What else can I try?

Regards,
Wes Aman

---

### Post by mikewhatever on 2011-10-11
Dell used to sell the Minis with Ubuntu 8.04-lpia. LPIA was Intel's low power architecture which is no longer supported. You can check yours with the **uname -m** command.
If the output is lpia, your only option is to reinstall, which really isn't a big deal.

---

### Post by Frogs Hair on 2011-10-11
Check your update manager settings per the instructions at the link .[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by saenger on 2011-10-11
> **mikewhatever said:**
> Dell used to sell the Minis with Ubuntu 8.04-lpia. LPIA was Intel's low power architecture which is no longer supported. You can check yours with the **uname -m** command.
If the output is lpia, your only option is to reinstall, which really isn't a big deal.


It IS -lpia, so I'll have to reinstall.  Thanks for the help.

---

### Post by saenger on 2011-10-11
> **Frogs Hair said:**
> Check your update manager settings per the instructions at the link .[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Thanks for the link.  I've downloaded 10.04 onto a USB stick, so I'll do a new install.

---

### Post by thatguruguy on 2011-10-11
> **doit said:**
> Download it on a different computer and burn the iso to a disk. Install Ubuntu 8.10 on that computer using the disk you made.

If I were you I would stick with Ubuntu 8.04 LTS, it's more stable than 8.10.

8.04 is no longer supported. For that matter, neither is 8.10.

The OP should either upgrade to 10.04 (the current LTS) or 11.04 (the current Ubuntu), or wait a couple days and upgrade to 11.10.  Suggesting he stay with 8.04 is bad advice.

---

