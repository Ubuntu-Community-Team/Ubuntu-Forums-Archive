---
title: "Is there a way to force to install/upgrade to ubuntu 14.10 from 14.04?"
date: 2015-04-09
forum: Installation &amp; Upgrades
---

### Post by Ashley_Smith on 2015-04-09
I tried updating my computer ubuntu system from 14.04 to 14.10, i clicked the wait button, and it shows the red triangle with an exclamation point and says there are updates but when i click show updates it says that everything is up to date. i was wondering how to update it to the latest version, it downloaded the stuff before but now i have no clue and cant find anything on how to update it or force it to update. what do i do? i'm new to ubuntu

---

### Post by plucky on 2015-04-10
> **Ashley_Smith said:**
> I tried updating my computer ubuntu system from 14.04 to 14.10, i clicked the wait button, and it shows the red triangle with an exclamation point and says there are updates but when i click show updates it says that everything is up to date. i was wondering how to update it to the latest version, it downloaded the stuff before but now i have no clue and cant find anything on how to update it or force it to update. what do i do? i'm new to ubuntu

Why do you want to update to 14,10?

14.04 is LTS (long Term Support)= 5 years, 14.10 is supported for 9 months.

If you open **Software and Updates** and go to **Updates** tab,at the bottom is "Notify me of new Ubuntu version", if you change that from LTS version to "For any new version",then the Update Manager will offer you the upgrade.

This assumes you are currently up to date in 14.04.

> it shows the red triangle with an exclamation point 

Open a terminal and post output for ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Good Luck

---

