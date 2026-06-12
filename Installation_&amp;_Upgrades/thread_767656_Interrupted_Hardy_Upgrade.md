---
title: "Interrupted Hardy Upgrade?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by kmand on 2008-04-25
I did an upgrade from Gutsy to Hardy via update-manager that got interrupted and rebooted. Update-manger won't come back up now missing pygtk which had presumably been removed during the interrupted upgrade.

Is there some way I can resume or restart the upgrade?

---

### Post by Partyboi2 on 2008-04-25
What happens when you
```
sudo apt-get dist-upgrade
```

---

### Post by kmand on 2008-04-26
> **Partyboi2 said:**
> What happens when you
```
sudo apt-get dist-upgrade
```

I had to first

dpkg --configure -a

to rebuild the database, but after that

apt-get dist-upgrade

seemed to work.

---

