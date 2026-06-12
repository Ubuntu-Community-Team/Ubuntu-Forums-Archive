---
title: "Preseed medium questions when priority=high"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by pashdown on 2011-05-19
I'm trying to preseed the installation of nslcd.  I would like the installer to ask for the nslcd/ldap-bindpw, but unfortunately, the priority of this in nslcd.config is "medium".  Going to priority=medium for the entire installer causes a boatload of useless questions to be asked.

It would be nice if I could go "priority=medium" for just the one nslcd package, or otherwise query for nslcd/ldap-bindpw.  I am tearing my hair out over this.  It seems the proper fix is that the priority on nslcd/ldap-bindpw should be "high" as it is rather essential for a secure ldap installation, but I can't wait a few distributions down the road for it to change.  Does anyone have an idea how to address this?

---

