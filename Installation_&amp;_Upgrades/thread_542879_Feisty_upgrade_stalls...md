---
title: "Feisty upgrade stalls.."
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by jhellman on 2007-09-04
Hello guys & gals,

I have problems updating my Ferrari 3400 from Edgy to Feisty Fawn.. I try to do it automagically with update manager (latest version)..

The upgrade starts fine.., but when download gets to: "fetching file 132 of 146", then it stalls and nothing moves after that.. after a couple of minutes there is error message "error during update" - "A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."

The information given in box below is as follows;

Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/edgy/Release.gpg](http://wine.lowvoice.nl/apt/dists/edgy/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/edgy/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/edgy/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/edgy/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/binary-i386/Packages.gz) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/source/Sources.gz](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/source/Sources.gz) Could not resolve 'nvidia.limitless.lupine.me.uk'
Failed to fetch [http://seveas.imbrandon.com/dists/edgy-seveas/all/source/Sources.gz](http://seveas.imbrandon.com/dists/edgy-seveas/all/source/Sources.gz) 404 Not Found
Failed to fetch [http://seveas.imbrandon.com/dists/edgy-seveas/all/binary-i386/Packages.gz](http://seveas.imbrandon.com/dists/edgy-seveas/all/binary-i386/Packages.gz) 404 Not Found

What should I do? Sorry for stupid question, but should I just take those lines out of sources file? Or am I missing some repositories needed?

This must be trivial, thanks for help to one who can help!

---

### Post by rsambuca on 2007-09-04
All of those repositories are non-standard ubuntu repositories.  For now I would just comment them out by placing a number sign in front of the lines in your /etc/apt/sources.list.  Keep in mind, if you have been using these repositories, there is a decent chance that the upgrade will not work, so you had better make sure you backup any sensitive data first.

---

### Post by jhellman on 2007-09-04
Thanks, I'll try that. This is not the system I use for work. I can always reinstall this one.

---

