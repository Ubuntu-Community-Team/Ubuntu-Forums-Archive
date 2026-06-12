---
title: "upgrade to 7.10 - update manager"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2007-10-20
but i get the following message - at the time of 
preparing the upgrade.

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/fiesty/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/fiesty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/fiesty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/fiesty/universe/binary-i386/Packages.gz) 404 Not Found

any idea - what is to be done? it says network connection - but internet is working fine at my end.

sandeep

---

### Post by Stemp on 2007-10-20
It's feisty not fiesty.
Fix this typo in your /etc/apt/sources.list ;)

---

### Post by mosaic2s on 2007-10-20
thanks. it worked, removed the third party from list.

---

### Post by mosaic2s on 2007-10-22
downloaded ok overnight. after that something failed. had to format disk and reload 7.04 from CD. sorry. could not locate bugs and report.

will wait for  7.10 CD before trying gutsy.

---

