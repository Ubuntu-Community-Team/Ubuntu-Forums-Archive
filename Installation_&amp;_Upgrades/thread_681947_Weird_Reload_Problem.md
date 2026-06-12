---
title: "Weird Reload Problem"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by zakaroo on 2008-01-29
So, this weekend I went to install a package (honestly I don't remember which one but it doesn't matter).  The package crashed my system badly, so I did a fresh re-install of 7.10.  I had a old backup of the packages from synaptic (I do this once a month or so).  I've used this package list before to reinstall on this PC.  Everything went fine - the packages all installed and everything seems to be working, except....That now the PC freezes periodically, I can't even hotkey a terminal window open, so have to COLDboot the PC.  This was a fresh install with a package list I've used on this PC before.  Anyone know of anyway that I can track down what is causing the hang?

---

### Post by hal8000 on 2008-01-29
You can have a look in /var/log/messages,  this is often useful, but if the freeze occurs before the log can be written to it may not reveal anything.

Sometimes backups are like waiting timebombs. I have a feeling that as your backup is a month old or longer, some package has either been installed from your backup and now requires different dependencies. See what other answers you get, but I would always update the apt and install online than from a backup.

---

