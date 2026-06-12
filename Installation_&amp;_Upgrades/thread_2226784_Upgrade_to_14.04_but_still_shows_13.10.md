---
title: "Upgrade to 14.04 but still shows 13.10"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by Matt_klimmer on 2014-05-29
Hi im running ubuntu 13.10 headless through SSH and today I did the dist-upgrade and it upgraded, it all went well no errors or anything but everything still says 13.10...What can i do to check this out or correct it?

---

### Post by plucky on 2014-05-29
> **Matt_klimmer said:**
> Hi im running ubuntu 13.10 headless through SSH and today I did the dist-upgrade and it upgraded, it all went well no errors or anything but everything still says 13.10...What can i do to check this out or correct it?

```
sudo apt-get dist-upgrade
``` will **not** get you to 14.04, you have to run ```
sudo apt-get install update-manager-core
sudo do-release-upgrade
``` to start the upgrade process.

See [Upgrades](https://help.ubuntu.com/community/Upgrades)

Terminal command ```
lsb_release -a
``` will tell you what release is installed.

Good Luck

---

### Post by Matt_klimmer on 2014-05-29
Alright, sounds good I will give it a try tonight...thanks

---

