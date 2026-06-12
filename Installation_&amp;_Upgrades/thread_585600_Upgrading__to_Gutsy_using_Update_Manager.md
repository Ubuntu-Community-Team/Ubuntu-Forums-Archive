---
title: "Upgrading  to Gutsy using Update Manager"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by mkeaneaz on 2007-10-21
I keep trying to upgrade to Gutsy using the update manager and i keep getting these error messages.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


if you have any information on how to get this resolved please let me know because i am going Nucking Futs trying to upgrade to Gutsy.

Thanks

Mike

---

### Post by linuxwizard on 2007-10-21
Try removing or disable extra repos you added to your source list. Than try upgrade again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

