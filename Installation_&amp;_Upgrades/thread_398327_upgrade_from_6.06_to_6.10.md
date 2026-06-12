---
title: "upgrade from 6.06 to 6.10"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by newbemac on 2007-03-31
I am Using 6.06 and want to upgrade to 6.10, can i do so from the ubuntu site and not lose by current software and installed apps?

---

### Post by aysiu on 2007-03-31
You don't do it from the Ubuntu site.

This will help you upgrade:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake)

By the way, the new version of Ubuntu comes out in a few weeks (7.04). You might want to wait until then and then do a clean reinstall. Reinstalling 7.04 will probably be faster than upgrading 6.06 > 6.10 > 7.04

---

### Post by chamberlain2006 on 2007-03-31
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades).  It will show you how.

---

### Post by newbemac on 2007-03-31
thanks, i will wait for 7.04

---

### Post by aysiu on 2007-03-31
I think your best bet is this:

1. [Create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome). This will allow you to reinstall Ubuntu while keeping your personal settings and files.

2. [Save a list of all the software you installed on top of the regular packages.](http://www.ubuntuforums.org/showthread.php?p=1069593#post1069593).

3. Wait until Feisty Fawn (Ubuntu 7.04) is officially released. Reinstall Ubuntu 7.04 (being careful not to reformat your /home partition), and then use the list of software you installed to easily reinstall all that software. For some reason, the instructions I linked to say ```
apt-get dselect-upgrade
``` I think you might have to do ```
sudo apt-get dselect-upgrade
```

---

