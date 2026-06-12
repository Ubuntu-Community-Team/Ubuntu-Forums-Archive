---
title: "Add packages manually into local mirror"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by feutete on 2013-01-15
I have used apt-mirror to create a local mirror of lucid and precise to support my company's servers. I do not want to use cron to keep it up to date, as my company requires us to first certify each package that gets installed rather than enabling automatic updates (security or otherwise). 

My question is, what is the best way to manually get a package into my mirrors? For example, if an update to openssl is released, how do I get just the updated openssl into my mirror without re-running apt-mirror, which would also retrieve all other packages that have been updated since my last sync?

---

