---
title: "[SOLVED] Error upgrading to Gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by headflux on 2007-10-18
Hi

When upgrading to Gutsy from Feisty using the update manager, I get the following error message:


```
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg Could not resolve ‘wine.lowvoice.nl’
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2 Could not resolve ‘wine.lowvoice.nl’
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz Could not resolve ‘wine.lowvoice.nl’
```


Please can anyone offer any help?

Thanks in advance

---

### Post by linuxwizard on 2007-10-18
Try disabling/or remove your extra repo in your source list.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by headflux on 2007-10-19
Thanks LinuxWizard, that got me past the problem, upgrade now in progress.

Moral to the story... 'read the manual!' :)

---

