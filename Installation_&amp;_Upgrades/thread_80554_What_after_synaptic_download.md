---
title: "What after synaptic download"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by CassioBunana on 2005-10-22
Hi! I want to upgrade from Hoary  to Breezy and I followed the suggestion I found somewhere here in the forum: change hoary to breezy in aptget conf and start synaptic......well it seems to work well...a lot of packages to be download....


So I did it, waited long time and next?? After reebooting I can't feel differences...same bugs, same device drivers problems...have I missed somethings? 

Why if I do "uname -r" I get the previous kernel verison?

I doesn't seem to be really updated.....


Andrea

---

### Post by DJ_Max on 2005-10-22
It doesn't sound like you completed the upgrade. Run
```
sudo apt-get -f install
```

There may have been a dependency problem you didn't look at. Then try to dist-upgrade again.

---

