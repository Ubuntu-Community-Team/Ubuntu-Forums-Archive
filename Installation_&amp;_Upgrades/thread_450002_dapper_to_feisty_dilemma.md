---
title: "dapper to feisty dilemma"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Lary Grant on 2007-05-20
Hi... I have Dapper running on 2 machines at home.  They are working really well, but I would like to upgrade to feisty.  As I understand it, if I want to officially "upgrade", I have to upgrade to Edgy, then to Feisty.

I have the impression that upgrading is not ideal, because you may not get the best configuration, because the upgrade process tries to retain whatever software and configurations you have. Even though you may not be so particular about keeping that software or configuration, the upgrade process has no way of knowing that.  So the upgraded system ends up being a compromise between your old configuration and the latest version.  Doing 2 upgrades magnifies this effect.  Please correct me if I'm wrong in this.

My other option is to install Feisty from scratch.  But then I have to worry about what files exactly to back up from my Dapper system and restore once I have Feisty installed.

Any advice?

---

### Post by tgoose on 2007-05-20
So long as you copy the entirity of your /home directory across, you will retain all documents and in principle all settings. It could be that some software has changed enough in the last year not to read old configurations perfectly, but that shouldn't happen.

Ideally you should have /home on a separate partition to the root partition, because then you can just run the Feisty install CD, tell it to overwrite the root partition and use the correct partition without overwriting it, because then you don't have to manually transfer any files (although backups are of course a good idea!) For some reason the Ubuntu installer doesn't partition like this by default...

---

