---
title: "Issue upgrading web server from 15.04 to 20.04 : Apache packages"
date: 2020-07-20
forum: Installation &amp; Upgrades
---

### Post by anz000 on 2020-07-20
We have a server running 15.04. We deploy a rails application there. I wanted to upgrade the server to 20.04.

We  use a rails deploy script to deploy our application. When I attempt  this on a 20.04 machine, the deployment fails because of some missing  apache packages. When I bypass those packages, the deploy fails, as  expected, due to some missing configuration files.

I haven't  worked much on configuring apache web servers, but I'd like to know if  those missing packages have been migrated to some other packages. Some  general information on those packages would also be much appreciated.  Thanks.

The packages are **"apache2-mpm-prefork" [SIZE=2]and[/SIZE] "****apache2-prefork-dev".**

---

### Post by CatKiller on 2020-07-20
That module is included in [apache2-bin](https://packages.ubuntu.com/focal/amd64/apache2-bin/filelist).

Using 15.04 was a mistake. Support for that ended in February 2016. If you'd used 14.04, you'd have had support till April 2019, giving you plenty of time to upgrade to 16.04 or 18.04, which are still supported. If you want long term support then you need to use a Long Term Support release. At least you're moving to an LTS release now.

---

