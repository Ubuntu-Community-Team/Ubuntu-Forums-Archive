---
title: "Update or install?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by frisket on 2007-04-23
OK, so it's time to upgrade to Feisty from Edgy. I can either click on Upgrade to 7.04 next time my update manager offers it, or type gksu "update-manager -c", or I can burn the ISO and start over.

What are the differences? 

a. Will using the Upgrade link make it re-detect my hardware from scratch, or will it believe the settings I already have from Edgy (which work, but which may not be optimal for Feisty)?

b. Will Upgrade preserve my config files in /etc and elsewhere or will I have to copy them all back from backup afterwards?

c. Almost everything I use was installed via Synaptic, but a handful of stuff was compiled from GNU sources (into /usr/local/{bin|lib}) or were downloaded binaries (in /usr/local/...). Will Upgrade trash this or preserve it?

I haven't been able to find a page describing what Upgrade keeps and what it changes/deletes.

---

### Post by ayenack on 2007-04-24
Well there are only two choices here. What I would do is back up all critical data that I did not want to lose and update then if all goes wrong you can install a fresh copy and if that is no good just re-install Edgy and restore all critical data.

Best of luck. ayenack.

---

