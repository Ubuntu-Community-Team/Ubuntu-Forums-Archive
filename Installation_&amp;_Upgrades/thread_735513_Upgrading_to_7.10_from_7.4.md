---
title: "Upgrading to 7.10 from 7.4"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by Paracelsus on 2008-03-25
Im trying to upgrade my Ubuntu to 7.10 from 7.4 and everytime I click the upgrade button in the Update manager I get the following errors.

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

My network connection is fine and I noticed that the errors I recieved were for wine, what can I do to upgrade my os? 

Thanks:confused:

---

### Post by Pumalite on 2008-03-25
Remove all third parties from your /etc/apt/sources.list and try again.

---

### Post by Paracelsus on 2008-03-25
That did the trick thanks.

---

