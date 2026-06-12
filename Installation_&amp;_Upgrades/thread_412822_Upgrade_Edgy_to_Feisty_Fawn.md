---
title: "Upgrade Edgy to Feisty Fawn"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Kuoi on 2007-04-18
Hello ,

I'm planning to download the full new version of Feisty Fawn this weekend.

I wander if I just can install it as an upgrade for Edgy , or is it not this way to do it ?

I have a seperate partition for my Home folder for the moment , and don't want to loose this.
How must I setup Feisty to make the Edgy Home folder as the new Feisty home folder ?

For example my é-mails in Evolution , when I setup Evolution in Feisty , Will it not overwrite my "Evolution" folder at my Home drive , and make the folder empty ?

I'll try to make a backup of most of my folders in Home , but just wanted to know if Feisty will not overwrite all this.

Greetings , and looking out for this weekend , hope it will be worth it.
Kuoi

---

### Post by heimo on 2007-04-18
Backup your system and upgrade using these instructions. There's no need to tell which partition is for home, because in upgrade you don't need to setup mount points or repartition - or format any partitions.
[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

### Post by sargeras on 2007-04-18
I did my upgrade (edgy to feisty) by just changing the repositories in /etc/apt/sources.list .  I just changed all instances of "edgy" to feisty" and did a apt-get update && apt-get upgrade (as root).  Before doing this, make sure that your system is fully updated.  The upgrade, by default, will use your edgy home directory for the feisty home.

Regards

---

