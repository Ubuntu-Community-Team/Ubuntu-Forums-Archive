---
title: "Breezy to Hoary?"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by Dragonfly_X on 2007-01-17
Hi Guys!

I've been trying to install Edgy on my pc at work using VWware, but upon clicking install the hole thing freezes. So, what i've tried to do now is install breezy and try to upgrade to Edgy but it creates some sort of depency problem and gksu "update-manager -c" doesn't work. 

I then tried upgrading to Hoary bu changing the repositories and runing sudo apt-get dist upgrade but it just returns " 0 to install, 0 to upgrade, 0 fixed"

Any ideas? ](*,)

---

### Post by bapoumba on 2007-01-17
Hello,
Hoary is a release previous to breezy, so you cannot upgrade to it.
Upgrade to dapper ;)

---

### Post by mcduck on 2007-01-17
also, after changing the sources.list you need to run 'sudo apt-get update' to get apt check the available packages..

---

