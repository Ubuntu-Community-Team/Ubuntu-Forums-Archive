---
title: "Nautilus install problem"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by willowhisp on 2006-10-08
When I try to install nautilus, I get the following error:

error processing nautilus_2.14.1-0ubuntu9_i386.deb (--install):
 trying to overwrite `/usr/share/gconf/schemas/apps_nautilus_preferences.schemas', which is also in package nautilus-data


Edit: Nvm, I managed to get it installed. For anyone interested, I extracted apps_nautilus_preferences.schemas, ran apt-get remove nautilus-data, and ran apt-get install nautilus.

---

