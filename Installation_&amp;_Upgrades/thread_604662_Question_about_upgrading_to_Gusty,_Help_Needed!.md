---
title: "Question about upgrading to Gusty, Help Needed!"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by mattmagician on 2007-11-06
Alright, so my Update Manager says that version 7.10 is available. COOL! So i click it, and wait. 
i get this error: 
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


Any help? I'd really like to upgrade. thanks!

---

### Post by bulldog on 2007-11-06
Make your sources.list default and remove all the extra repo's you added.
Also it could be wise to remove all programs which are installed from outside the official repo's.
Otherwise there's a fair chance your upgrade will fail.

---

### Post by mattmagician on 2007-11-06
I'm not exactly a Ubuntu wiz, so if you could lemee know how to do that it'd help. chances are i added them by mistake before >,<

---

### Post by bulldog on 2007-11-06
In that case it could be better to install Gutsy as an extra instead doing an upgrade,that is if you have a 10GB available on your hdd.
If Gutsy fails you have still a working copy of ubuntu.

Or do a clean install with the live cd or better the alternate cd.
It should definitly be quicker than an upgrade.:)

---

