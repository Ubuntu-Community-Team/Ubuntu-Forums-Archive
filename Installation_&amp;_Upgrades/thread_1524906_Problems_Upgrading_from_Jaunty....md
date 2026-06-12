---
title: "Problems Upgrading from Jaunty..."
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by Pateris on 2010-07-05
I decided I should finally upgrade from Jaunty to Lucid, and discovered that I first had to upgrade to Karmic (9.10).  OK

But when I started the upgrade process from the desktop, I started getting a lot of errors of the type:

"Cannot delete file /usr/share.dpkg-new"

And a repeated request to select either gdm or kdm as the default display manager...

A quick search led me to the problem being that the /usr mount point had been mounted read-only - apparently because ext3 does that if it has a problem.

Unfortunately, I couldn't fix it part way through the upgrade because /usr was in use by too many processes.  When I tried the brute force method, I forced a restart and then the restart locked up (failed) along the line...

Am I stuck reinstalling from scratch?

---

### Post by mörgæs on 2010-07-07
The machine does not sound healthy, so always go for a clean install. One hour, problem solved.

---

