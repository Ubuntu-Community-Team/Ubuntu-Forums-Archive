---
title: "Update Manager Network problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by professorchaos on 2007-10-20
When checking for updates with Update Manager I get the following message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found

This also prevents me from upgrading to 7.1.

---

### Post by linuxwizard on 2007-10-20
Try removing or disable extra repos you added to your source list. Than try to update again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by professorchaos on 2007-10-20
> **linuxwizard said:**
> Try removing or disable extra repos you added to your source list. Than try to update again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)Well then how do I update third-party software?

---

### Post by professorchaos on 2007-10-21
Ohnohebumpedit.

---

### Post by 4Foot on 2007-10-21
Professor:

You will find that there are new repositories for  medibuntu to use with Gutsy. So delete those old ones and start with the new. 

Such as [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free nonfree

Good luck

4Foot

---

### Post by professorchaos on 2007-10-24
> **4Foot said:**
> Professor:

You will find that there are new repositories for  medibuntu to use with Gutsy. So delete those old ones and start with the new. 

Such as [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free nonfree

Good luck

4FootSuccess! Many thanks.

---

