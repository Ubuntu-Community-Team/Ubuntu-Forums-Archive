---
title: "Upgrading to Edgy hangs at &quot;Preparing the upgrade&quot;."
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by inunguak on 2007-03-12
I have Dapper and tried to upgrade to Edgy using *gksu "update-manager -c"*, but it hangs at "Preparing the upgrade".  It said it could not fetch a file from [http://free.contrib](http://free.contrib).. something (sorry, I do not have the exact error message right now) and that there might be a network problem.  I disabled the firewall and tried it again, but I got the same error.

What am I doing wrong?

---

### Post by zvacet on 2007-03-12
```
gksudo gedit etc/apt/sources.list
```
Put # in the bigining of line with [http://free.contrib](http://free.contrib) . Save file and try again.

---

