---
title: "Upgrading from 11.10 to 12.10?"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2012-10-22
Hi,
I am presently running 11.10 and want to upgrade.  Is it possible to upgrade directly to 12.10, or do I need to upgrade to 12.04 first?

I also read somewhere that that 12.10 now requires a dvd install disc as opposed to a cd.  Yes or no?

Thx

---

### Post by Pilot6 on 2012-10-22
You can upgrade only to 12.04.

---

### Post by craigsn on 2012-12-18
Is there any way to do that from the command line, or do I have to download the ISO, build a CD/DVD and then update to 12.04?

---

### Post by Cheesemill on 2012-12-18
First make sure your system is fully updated:
```
sudo apt-get update
sudo apt-get dist-upgrade
```Then to perform the upgrade:
```
sudo do-release-upgrade
```It's always a good idea to have a full backup of your system first in case anything goes wrong with the upgrade. Also bear in mind this is a one way process, there is no way to roll back to a previous version.

---

### Post by Frogs Hair on 2012-12-18
Open the update manger > settings > check for new releases. Run the update manager and the upgrade should be offered.Look at the link before proceeding. [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

