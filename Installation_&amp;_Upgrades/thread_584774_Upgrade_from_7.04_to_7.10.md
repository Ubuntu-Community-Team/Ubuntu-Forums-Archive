---
title: "Upgrade from 7.04 to 7.10"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by gbrook on 2007-10-21
I tried upgrading from Update Manager and get this message and then it goes no further

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_AU.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_AU.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

I downloaded the iso and burnt a disc - inserted it and nothing occurred except it mounted and I can see all the files.

I then tried gksu "sh /cdrom/cdromupgrade" as indicated on the upgrade pageand nothing happened.

I would really like to uprade anyone able to help?

Cheers
Garry

---

### Post by Dr. Nick on 2007-10-21
before you update it remove any 3rd party repos. It looks like wine.lowvoice site is down and its stopping your upgrade.

---

