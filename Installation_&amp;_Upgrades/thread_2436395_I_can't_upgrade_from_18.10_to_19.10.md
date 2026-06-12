---
title: "I can't upgrade from 18.10 to 19.10"
date: 2020-02-05
forum: Installation &amp; Upgrades
---

### Post by hackerapollo on 2020-02-05
It says that my version is unsupported, but I want to upgrade. How do I do this?

---

### Post by CelticWarrior on 2020-02-05
Better to install fresh.

First of all you can't skip releases except when it's from one LTS to another. Not applicable in your case because neither are LTS. You'd have to follow the 18.10 > 19.04 > 19.10 route. And considering 18.10 and 19.04 are out of support and have no online repositories available - reason why you can't upgrade right now without making a lot of changes (re-directing the repositories to their archived versions) - the amount of work needed and the time wasted would be insane. 

Do your backups and install from scratch, it's that simple.

---

### Post by TheFu on 2020-02-05
> **CelticWarrior said:**
> Better to install fresh.
 <snip>
Do your backups and install from scratch, it's that simple.

Good advice.  Also, best to stay on only LTS releases if you cannot commit to upgrading every 6 months, without delay.
The cadence of Ubuntu releases is well-understood AND well-published.
April of even years are LTS releases.  Usually, best to wait until July to install the fresh LTS so the 150 or so missed bugs are closed before we touch it.
See the graph here: [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)
18.10 is long dead.

---

### Post by guiverc on 2020-02-05
Most of this I'd hope is already know, touching on that already provided.

18.10 means the 2018-October release; ie. you have 9 months from then so easy to calculate.
19.04 is the next release; the only release 18.10 is tested to upgrade to, thus only supported upgrade; this appears 6 months after the prior release (the six months mentioned earlier).  You have 3 months from 19.04's release to make the jump though; ie. upgrade must occur 6-9 months from release.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

An option for you is 
 - backup your data
 - install 19.10 using [I]something-else
   -- [/I]use existing partitions but ensure you don't have 'format' checked
   -- it will take a note of your additional software
   -- erase system directories
   -- install system
   -- add back your additional software (if available in repos)
   -- it won't touch user files (unless 'format' was checked)

Note because it erases system directories, some server config files can be lost (where kept in system directories).  This isn't an issue with desktop applications generally (which store configs in $HOME directories) but it's up to the programmer where they stored *conf* files.  Backups are essential

---

