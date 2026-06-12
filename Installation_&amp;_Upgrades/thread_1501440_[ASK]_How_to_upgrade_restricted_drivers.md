---
title: "[ASK] How to upgrade restricted drivers"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by squiddy on 2010-06-04
Hi,

If we take a look at this repository mirror, [ftp://ftp.jaist.ac.jp/pub/Linux/ubuntu/pool/restricted/f/fglrx-installer/](ftp://ftp.jaist.ac.jp/pub/Linux/ubuntu/pool/restricted/f/fglrx-installer/) then we could see newer version of fglrx drivers.

They would be:
fglrx-amdcccle_8.723.1-0ubuntu4_i386.deb
fglrx_8.723.1-0ubuntu4_i386.deb

My installed restricted drivers are:
fglrx-amdcccle_8.723.1-0ubuntu3_i386.deb
fglrx_8.723.1-0ubuntu3_i386.deb

My question is, why doesn't the update manager tell me that there are newer files on the repo mirror so i can update them?

---

### Post by davidmohammed on 2010-06-04
generally, someone will need to load the driver into the repo.  This being the LTS though, I guess there will have to be a major pressing need for new updated drivers to come through.

If you can't wait, I'm sure there must be a ppa around where someone is playing with the latest and best.

---

### Post by squiddy on 2010-06-04
are you saying that, the newest driver that listed on the repo mirror isn't really the official updates?

---

### Post by davidmohammed on 2010-06-04
no - just saying when new drivers come along then it is not always the case that they get uploaded.

In the case of mirrors - it can take some time, sometimes days for all mirrors to sync.  You could always point your software sources (download from dropdown and select others) to get your repository from somewhere else.

---

