---
title: "Selective upgrading from hardy-proposed"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by bruce89 on 2008-06-08
I've found a way of being able to install select packages from hardy-proposed but without update-notifier finding out.

Create the file /etc/apt/preferences with this content:
```
Package: *
Pin: release a=hardy
Pin-Priority: 900

Package: *
Pin: release a=hardy-proposed
Pin-Priority: 400
```

You can then start aptitude to select the -proposed packages you want to upgrade with ```
sudo aptitude -t hardy-proposed
```

This means you won't be prompted to upgrade all the -proposed packages, only ones you want to upgrade.

---

### Post by bapoumba on 2008-06-08
Moved to Installation & Upgrades.

Thanks bruce89 for this tip with the preference file.
May I add a warning ? Using update-manager or synaptic is using apt-get. I would not recommend using aptitude and apt-get (or the GUI) on the same install, as they do not share infos regarding their actions. You can end up with surprises :)

---

### Post by FuturePilot on 2008-06-08
Hey this is cool. Thanks. :)

---

