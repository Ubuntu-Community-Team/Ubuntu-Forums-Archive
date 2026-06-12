---
title: "Holding all related packages"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by shorn1986 on 2012-11-06
I want to do security updates for a Server but do not want certain packages to be updated because they may cause compatibilities for some custom software.

One such package is Mysql 

echo package_name hold | sudo dpkg --set-selections 
holds specific package names from being updated.

Now there are many packages related to mysql like
mysql-common, mysql-server

How do i hold all this packages from being updated.
Do i need to hold each package one by one

Cheers
Shorn

---

