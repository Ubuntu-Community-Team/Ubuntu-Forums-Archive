---
title: "Upgrading from 17.04 to 17.10"
date: 2018-04-03
forum: Installation &amp; Upgrades
---

### Post by Shouyryuu on 2018-04-03
I've been trying to upgrade from ubuntu 17.04 to 17.10.

I do not get an automatic prompt although I've requested so in the updates settings, and so am using /usr/lib/ubuntu-release-upgrader/check-new-release-gtk in the terminal.

The updater launches but I get the following error:
E:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/artful/InRelease](http://archive.ubuntu.com/ubuntu/dists/artful/InRelease)  Unable to find expected entry 'partner/source/Sources' in Release file (Wrong sources.list entry or malformed file), E:Some index files failed to download. They have been ignored, or old ones used instead.

The error prompt suggests that I might have connectivity issues but everything seems to be working fine with regards to my internet connection.

Any advice?

---

### Post by wildmanne39 on 2018-04-03
That is because 17.04 reached EOL, which means it is no longer supported and the repositories have been removed so your best course of action is to back up important data and install 16.04 then you can directly upgrade to 18.04 when it comes out on the 26th of this month if you wish or you can wait until it comes out and install 18.04 directly but your system will be at risk because you are no longer receiving security updates.

---

### Post by Shouyryuu on 2018-04-08
Ah! Thank you!

I've been noticing a lot of lag/issues when playing videos from flash players (mostly twitch). Am hoping a new install will solve these.

---

