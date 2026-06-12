---
title: "is it possible to do a &quot;do-release-upgrade&quot; to Hardy from a CD image?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by f0rbl3 on 2008-04-23
Is it possible to do a LTS server upgrade from Dapper to Hardy using "do-release-upgrade", but point it to a CD image or directory tree, instead of having the upgrade download everything on each machine over the Internet?

I have several headless machines without CD drives or screens, running Dapper LTS.

I've tried searching for an answer to this, but can't seem to find an answer...

Thank you!

---

### Post by FakeOutdoorsman on 2008-04-23
[_Upgrade from 6.06 LTS to 8.04 LTS_]("https://help.ubuntu.com/community/HardyUpgrades")
[URL="http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/"]
_Dapper To Hardy Direct Server Upgrade Works!_[/URL]

You can use [_apt-proxy_]("https://help.ubuntu.com/community/AptProxy") to update headless computers while only downloading the required packages once.  I'm not sure if you can use it with the disc at the same time.

---

