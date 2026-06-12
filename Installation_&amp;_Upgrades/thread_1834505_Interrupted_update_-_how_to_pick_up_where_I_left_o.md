---
title: "Interrupted update - how to pick up where I left off?"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by CoolBreeze47 on 2011-08-27
Hi everyone

I have Kubuntu 11.04 and was in the process of installing the KDE 4.7 update via the PPA and all of the packages downloaded just fine but only about half of them installed before I accidentally interrupted the update.

Rebooting was no problem but I'd like to make sure that all of the downloaded updates actually installed. Is there a way to pick up where I left off and install the remaining packages from the update that were not installed due to the interruption?.

Thanks so much for your help!.

- CB

---

### Post by raja.genupula on 2011-08-27
open your update manager , its gonna show the remaining updates which are to be installed .

---

### Post by Old_Grey_Wolf on 2011-08-27
Or enter these commands in the terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you get errors, post the errors back to this thread using the CODE tags. Click the # icon and past between the tags.

---

