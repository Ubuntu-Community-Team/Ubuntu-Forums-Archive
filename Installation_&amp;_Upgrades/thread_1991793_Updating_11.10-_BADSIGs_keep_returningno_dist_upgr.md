---
title: "Updating 11.10- BADSIGs keep returning/no dist upgrade in Update Mngr"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2012-05-31
Hi all!  ... Having some problem with updates on 11.10.

First of all, when I do an update, I get a lot of this:

> The following signatures were invalid: BADSIG xxxxxxxxxxI can fix that with:

```
sudo aptitude clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial
sudo aptitude clean  
sudo aptitude update
```Once done, sudo aptitude upgrade returns nothing, as the system is up
to date.  Running the update manager confirms that.  The odd thing is, 
I don't see any sign of an available distribution upgrade, even though 
Settings>>Updates has "Notify me of a new Ubuntu version" set to "For 
any version"; and "When there are new updates" is set to "Display Immediately".
 Furthermore, when I try sudo aptitude update again, I start getting the BADSIGs 
all over again.

Can anybody give me some clue what's up?
Thanks!
DA

---

### Post by dino99 on 2012-05-31
open up /etc/apt/sources.list, disable the third parties (if any), change "oneiric" by "precise" and save that file. Then update/upgrade

---

