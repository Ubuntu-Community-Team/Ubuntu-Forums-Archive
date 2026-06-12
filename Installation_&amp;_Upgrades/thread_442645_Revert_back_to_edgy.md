---
title: "Revert back to edgy?"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by stembot on 2007-05-13
Firefox is a pile of poop after the upgrade.  I wish I had read around first before blindly upgrading. 

How do I revert back to edgy?

---

### Post by mlind on 2007-05-13
This might screw your system even more, but it's worth a try


Define these in /etc/apt/preferences
```

Package: *
Pin: release a=edgy
Pin-Priority: 1001

Package: *
Pin: release a=edgy-updates
Pin-Priority: 1002

Package: *
Pin: release a=edgy-security
Pin-Priority: 1003

Package: *
Pin: release a=edgy-backports
Pin-Priority: 1001

```

Then try to simulate downgrading a distribution
```

sudo apt-get -s dist-upgrade

```

If the output looks good, then actually do it
```

sudo apt-get dist-upgrade

```


Make sure you have edgy repositories defined in /etc/apt/sources.list

---

### Post by tgalati4 on 2007-05-13
Is it possible to just downgrade to Firefox 1.5.0.11?

---

### Post by mlind on 2007-05-13
> **tgalati4 said:**
> Is it possible to just downgrade to Firefox 1.5.0.11?

yeah, probably easiest way would be download a copy from mozilla.org and use that locally. Otherwise you'd need to rebuild Edgy's firefox (+locales) for Feisty.

---

