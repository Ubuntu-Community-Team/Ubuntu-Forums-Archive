---
title: "how to upgrade from 6.02 to 7.04 feisty"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by JayDeePlus on 2007-04-10
i did not mean to download dapper, i actually was wanting feisty and i did not know the versions for each. i now have dapper and is wanting to skip echy and go to feisty. how should i do this.

also i would like to know how to get the beryl package install onto it aswell.

---

### Post by mac.ryan on 2007-04-10
If you look on the official ubuntu.com site, you will notice the upgrade system can only work between contiguous releases. Therefore, if you want to update your system, you should update twice: dapper to edgy, edgy to feisty.

Alternatively, you could reinstall ubuntu. In order to preserve your settings, users, groups, etc... you should manually save and then restore various directories. If you choose to go this way, search on the forums first: it is not a 100% safe way, and you can fetch lot of good advices in past threads.

---

### Post by JayDeePlus on 2007-04-10
how do you upgrade dapper to edgy?

---

### Post by ittiam on 2007-04-10
The way i upgraded was changing the word dapper to edgy in sources.list. and do a
apt-get update
apt-get dist-upgrade!

---

### Post by raul_ on 2007-04-10
> **ittiam said:**
> The way i upgraded was changing the word dapper to edgy in sources.list. and do a
apt-get update
apt-get dist-upgrade!

Well, that way, according to the Ubuntu webiste, youhave to do "dist-upgrade" twice...don't ask me why.

you can just run "sudo update-manager -c"

---

### Post by mac.ryan on 2007-04-10
Here the recommended method and the alternate ones:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by JayDeePlus on 2007-04-10
ok that sudo update-manager -c code worked and it's now upgrading to edgy.

whats the recommendation on going from edgy to feisty? and is it's stable how do you upgrade from edgy to feisty? will that last link let me know how?

---

### Post by JayDeePlus on 2007-04-10
also how do you get the beryl package for feisty? and is beryl supported on feisty?

---

### Post by zvacet on 2007-04-11
Right now you can upgrade to Feisty Beta.Wait for couple weeks and you will be able to upgrade to final version of Feisty.I think you are not in some kind of hurry.

---

