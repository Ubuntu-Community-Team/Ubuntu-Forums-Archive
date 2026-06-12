---
title: "upgrade 11.04 to 11.10 stopped but not clear why"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by tuskpc on 2012-01-21
Each time I try to upgrade from 11.04 to 11.10, I hit the same stumbling block.  Not having a working DVD drive, the only way I can upgrade is through the upgrade-manager; however I cannot find the specific item that is keeps it from upgrading.  Plus the manager does not show what the terminal is seeing so I am utterly clueless.  Any suggestions?

---

### Post by ajgreeny on 2012-01-21
Did you install any packages not from the standard repositories in your version of 11.04, eg from a ppa repository, or another place.  If so, that may be the stumbling block, so either uninstall those packages, and/or disable the ppa repos and try again.

---

### Post by tuskpc on 2012-01-21
I un-clicked the button for "Independent third party developers repository"

Upgrading the same thing happened:
Setting new Software Channels
Fetching 45 of 102 at 737 kB/s

Waited till the same warning I posted as an attachment reappeared.

How do I find out what number 45 is?

---

### Post by ajgreeny on 2012-01-21
> **tuskpc said:**
> I un-clicked the button for "Independent third party developers repository"

Upgrading the same thing happened:
Setting new Software Channels
Fetching 45 of 102 at 737 kB/s

Waited till the same warning I posted as an attachment reappeared.

How do I find out what number 45 is?
Sorry, but I'm not sure about that, though I am sure there must be a way.

Try running ```
sudo apt-get update > repos.txt
``` to see if it helps by showing where the problem was when you look through the repos.txt file in your home; maybe line 45?

---

