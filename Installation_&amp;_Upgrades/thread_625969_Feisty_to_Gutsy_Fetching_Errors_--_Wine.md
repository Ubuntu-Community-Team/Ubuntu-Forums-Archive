---
title: "Feisty to Gutsy: Fetching Errors -- Wine?"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by scriptoris on 2007-11-28
I'm trying to upgrade from Feisty to Gutsy, but I received this error. I read about third-party programs being virtually un-upgradeable, so I uninstalled Automatix and Wine and unchecked all the 3rd party software sources. Yet I still receive this message :confused::

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

---

### Post by linuxwizard on 2007-11-28
Remove or disable them in your source list. These repos you must have added.

---

