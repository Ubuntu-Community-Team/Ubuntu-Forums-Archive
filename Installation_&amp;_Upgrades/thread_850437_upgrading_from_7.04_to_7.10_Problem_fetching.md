---
title: "upgrading from 7.04 to 7.10 Problem fetching"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Icenate001 on 2008-07-05
Hello everyone, I have a problem upgrading, now i read previous posts about uninstalling repositories when it has a problem fetching data when downloading updates.I am trying to update  from 7.04 to 7.10 and soon to 8.04 or the new one. I keep getting this error 

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

what should i do?

---

### Post by kostkon on 2008-07-05
> **Icenate001 said:**
> Hello everyone, I have a problem upgrading, now i read previous posts about uninstalling repositories when it has a problem fetching data when downloading updates.I am trying to update  from 7.04 to 7.10 and soon to 8.04 or the new one. I keep getting this error 

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

what should i do?
Go to *System -> Administration -> Software Sources* and remove this repository. Then try again to upgrade.

---

### Post by bapoumba on 2008-07-05
> **kostkon said:**
> Go to *System -> Administration -> Software Sources* and remove this repository. Then try again to upgrade.
Do not forget to reload before upgrading again.

---

### Post by Icenate001 on 2008-07-05
actually i think i solved it.. but at the cost of uninstalling wine... :(  then i went back and al of a sudden a new repository was listed wine something or other.. I dont know why it showed up all of a sudden but i am now updating thanks for the advice

---

