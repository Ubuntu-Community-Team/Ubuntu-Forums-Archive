---
title: "Upgrading to Edgy problem"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by DarkOdysseus on 2007-03-18
First off, I dont know what version I am using. I installed Dapper Drake from an old live cd and then installed around 232 updates so at this moment I dont know what version I am using. Now when I go to my update manager it says I dont need any updates and there isent a choice to upgrade to Edgy Eft. While following instuctions on installing xgl on gnome for Edgy Eft, alot of the instuctions were not corresponding with my system. Is there anyway to find out what version I am using and if I still do have Dapper Drake, can someone tell me a way to upgrade to Edgy Eft.

thanks much

---

### Post by Kateikyoushi on 2007-03-19
This command should tell you which version do you use.
```
lsb_release -a
```

Read this on how to upgrade. [LINK]("https://help.ubuntu.com/community/EdgyUpgrades")

If you get stuck show us your sources.list
```
cat /etc/apt/sources.list
```

---

