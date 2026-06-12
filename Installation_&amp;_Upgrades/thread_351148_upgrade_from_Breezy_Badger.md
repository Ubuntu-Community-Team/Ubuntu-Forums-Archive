---
title: "upgrade from Breezy Badger"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2007-02-01
I have Breezy Badger on a dual boot system, but have not used it in about a year. What is the easiest way to upgrade directly to 6.10? I hope this can be done without messing around with partitions and grub etc.

Also, I forgot all the commands and keyboard shortcuts etc. Someone please direct me to a page that summarizes all the basics to get re-familiarized.

TIA.

---

### Post by bscbrit on 2007-02-01
Edit your repos file (/etc/apt/sources.list) and replace every 'breezy' with 'edgy'.  Then use either Synaptic or in a terminal type:

sudo apt-get update
sudo apt-get dist-upgrade


If you experience problems after the upgrade, run

sudo apt-get update
sudo apt-get xserver-xorg

Some people have found that the xserver does not install cleanly the first attempt but is picked up by the second.

---

### Post by WW on 2007-02-01
bscbrit: Are you sure about that? According to the wiki, you can only upgrade to Edgy from Dapper.  So, as I understand it, an upgrade from Breezy requires two upgrades: Breezy->Dapper, then Dapper->Edgy.

merlin666: Check out these wiki pages.
For Dapper->Edgy: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
For Breezy->Dapper: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

I used the update-manager to upgrade from Breezy to Dapper, and it worked pretty well.

---

### Post by bscbrit on 2007-02-02
I had no problems other than the installation of xserver-xorg.  But if the wiki suggests that you should go via dapper to edgy then do so.

Alternatively, if you have your /home on a separate partition, simply burn yourself an edgy install disk and do a fresh install. 

Note that Dapper has a long term support cycle whereas Edgy will be upgraded at the usual 6-monthly cycle.  Dapper is considered by many therefore to be more stable and reliable although I am not aware of any major issues with Edgy.

---

