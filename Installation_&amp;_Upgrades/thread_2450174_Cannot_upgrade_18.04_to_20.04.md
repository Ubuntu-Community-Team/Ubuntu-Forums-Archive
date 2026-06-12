---
title: "Cannot upgrade 18.04 to 20.04"
date: 2020-09-08
forum: Installation &amp; Upgrades
---

### Post by tokugawa-ieyasu on 2020-09-08
Hello everyone :biggrin:

I want to upgrade from 18.04 to 20.04.
Actually, I already wanted to upgrade already when 20.04 originally came out, but on the official update page it states:

> **From 18.04, upgrades will not be enabled until approximately the date of the 1st 20.04 point release at the end of July.**

So I tried upgrading beginning of August the first time.
I got all updates installed, so no problem there.

I tried the first option offered to upgrade:

> Ensure that the package ubuntu-release-upgrader-qt is installed.

Run in Krunner:
pkexec do-release-upgrade -m desktop -f DistUpgradeViewKDE

After this, exactly [SIZE=6]nothing[/SIZE] happened. No dialog, no message, nothing at all. Waiting for up to quarter of an hour did nothing as well.
I tried it several times, with rebooting, re-installing the package... still nothing at all.

So I tried the second method offered:

> Alternatively if you wish to do the entire upgrade in a terminal, in Konsole do:

sudo do-release-upgrade -m desktop

This finally offered me a hint why nothing happened: *(translated from German)*

> New releases of Ubuntu are searched
No LTS versions are avaiable.
To upgrade to the newest non-LTS version:
Set Prompt=normal in /etc/update-manager/release-upgrades

So I thought, okay, they still need a bit longer for it.
I tried several times throughout August, but still nothing.
For the last time, I tried today, but the upgrader still says there are no LTS versions available for upgrade.

This seems a bit fishy to me... is it still not possible to upgrade from 18.04 to 20.04?

---

### Post by Bashing-om on 2020-09-08
tokugawa-ieyasu; Hello

The upgrade path is presently blocked - testing continues by the development team.
Now, if you really want to upgrade now -
```

sudo do-release-upgrade -d

```
where 'd' is (D)evelopment - as until the block is removed 20.04 will maintain the development status. As "testing" breakage could occur.
Insure to reset to " Prompt=lts in /etc/update-manager/release-upgrades".

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Impavidus on 2020-09-09
Alternatively, you could fresh install 20.04.

---

