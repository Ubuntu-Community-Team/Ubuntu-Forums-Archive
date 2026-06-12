---
title: "How to upgrade ONE package?"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-03-21
I'm trying to find out how to do an upgrade of just ONE specific package, without causing an upgrade of anything else.  Also, I need to be able to do this from the command line, not GUI, possibly inside a script.  Locking all other packages to a specific version is not a practical option.  I have been using apt-get upgrade before, but that always upgrades everything.

What I have found so far is that I could use dselect to mark a package for upgrade, then have just the marked packages upgraded (the one I mark).  Upgrading what it depends on, if the dependency is for a newer version, is probably OK.  I have not tested this, yet, since I don't have the spare resources for it right now.  Is there a way to have dselect select ONE package for upgrade in a NON-interactive way?

The upgrades will be happening on server editions.

---

