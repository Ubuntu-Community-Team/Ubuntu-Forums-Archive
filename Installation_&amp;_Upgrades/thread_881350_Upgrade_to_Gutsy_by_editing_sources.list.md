---
title: "Upgrade to Gutsy by editing sources.list"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by iflanery on 2008-08-05
Just a quick question....

I have an HP Pavilion zx5000 running Kubuntu Feisty. Would it be possible to upgrade it to Gutsy simply by editing my sources.list, change each occurrence of "Feisty" to "Gutsy", and follow up with executing an aptitude update/upgrade? Or would that be a bit too quick and dirty?

---

### Post by zvacet on 2008-08-06
It is better to follow recommended way to upgrade.It is over net or from alternate CD.In both cases it is good to have separate home and back up your data.If you don´t have separate home make one following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.I prefer to use alternate CD because I allways have CD if I need it.Instructions for both ways are [here.]("https://help.ubuntu.com/community/GutsyUpgrades") If you want it is possible to do it like you asked.After you changed every feisty to gutsy

```
 sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```

```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

---

