---
title: "Upgrade crashed: Force Gutsy upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by AllesMeins on 2007-10-20
Hi,

my upgrade to gutsy crashed after approx. 60%. Now it seems I'm stuck between two versions. Some programs don't work anymore and adept informs me, that there is a version upgrade available. But I can't apply this upgrade, because distribution-upgrade fails (after presenting the list of no longer supported packages), informing me that my system is already up-to-date. Is there a way to force distribution-upgrade to ignore this version-check and simply do an upgrade. Or is there any other way for me to get a clean upgrade without reinstalling Kubuntu?

---

### Post by riksweeney on 2007-10-20
My Ubuntu wouldn't install via Adept Manager, so I did the following:

sudo apt-get update && sudo apt-get dist-upgrade

It told me that it couldn't install and to do

sudo apt-get -f install

This worked and then a

sudo apt-get dist-upgrade

finished off the install for me.

---

### Post by AllesMeins on 2007-10-20
That didn't do it for me. I get "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." after every step and adept still wants to do an version upgrade.

---

