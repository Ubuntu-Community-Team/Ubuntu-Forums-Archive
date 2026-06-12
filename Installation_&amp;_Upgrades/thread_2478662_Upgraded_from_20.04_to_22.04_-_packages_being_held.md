---
title: "Upgraded from 20.04 to 22.04 - packages being held back?"
date: 2022-09-01
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2022-09-01
I recently upgraded to 22.04 from 20.04 and get the following:

> 8 packages can be upgraded. Run 'apt list --upgradable' to see them.

sudo apt list --upgradeable
Listing... Done

gir1.2-gnomedesktop-3.0/jammy-updates 42.4-0ubuntu1 amd64 [upgradable from: 42.2-0ubuntu1]
gnome-desktop3-data/jammy-updates,jammy-updates 42.4-0ubuntu1 all [upgradable from: 42.2-0ubuntu1]
ldap-utils/jammy-updates 2.5.13+dfsg-0ubuntu0.22.04.1 amd64 [upgradable from: 2.5.12+dfsg-0ubuntu0.22.04.1]
libgnome-bg-4-1/jammy-updates 42.4-0ubuntu1 amd64 [upgradable from: 42.2-0ubuntu1]
libgnome-desktop-3-19/jammy-updates 42.4-0ubuntu1 amd64 [upgradable from: 42.2-0ubuntu1]
libgnome-desktop-4-1/jammy-updates 42.4-0ubuntu1 amd64 [upgradable from: 42.2-0ubuntu1]
libldap-2.5-0/jammy-updates 2.5.13+dfsg-0ubuntu0.22.04.1 amd64 [upgradable from: 2.5.12+dfsg-0ubuntu0.22.04.1]
libldap-common/jammy-updates,jammy-updates 2.5.13+dfsg-0ubuntu0.22.04.1 all [upgradable from: 2.5.12+dfsg-0ubuntu0.22.04.1]

When I perform a 'sudo apt upgrade', I get:

> sudo apt upgrade

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
**The following packages have been kept back:**
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data ldap-utils libgnome-bg-4-1
  libgnome-desktop-3-19 libgnome-desktop-4-1 libldap-2.5-0 libldap-common
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


Should I just let it be and it will self-correct over time or do I have to do something manually force complete upgrade?

Thanks

---

### Post by grahammechanical on 2022-09-01
There is no need to force anything. Ubuntu 22.04 might be the latest Long Term Support release but that does not mean that it is no longer under development. Ubuntu developers work to a 26 week release schedule. Gnome and Debian developers have their own release periods. It is not unknown for software from Gnome or Debian to be not ready for inclusion in a Ubuntu new release by the Ubuntu release date. Regular updating will sort this out.

Regards

---

### Post by &amp;KyT$0P# on 2022-09-01
> **michael351 said:**
> Should I just let it be and it will self-correct over time 

This, although there is nothing to "correct".  Those are phased updates that your system has not yet been phased into.  The installed versions you have of those packages are normal for Ubuntu 22.04.

---

### Post by michael351 on 2022-09-01
Cool! Thanks. Everything works as I need in the meantime.

---

