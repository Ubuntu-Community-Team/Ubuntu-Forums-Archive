---
title: "upgrade 14.04 to 15.10"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by thomas92 on 2016-02-17
Is there a way to upgrade from Ubuntu 14.04 to 15.10?

---

### Post by grahammechanical on 2016-02-17
Yes, and I will tell you how if you accept that Ubuntu 15.10 only has 9 months support which started at the end of October last year. That means that you will have to upgrade to Ubuntu 16.04 before the summer ends. Whereas, if you stick with Ubuntu 14.04 you can upgrade directly to 16.04 when it is released at the end of April this year. In fact the OS will notify you that there is an new LTS release available.

Go to System Settings>Software & Updates>Updates tab. You will see a panel labelled Notify me of a new Ubuntu version. It will be set to For long Term support versions. Change it to For any new version. And then run update manager/Software Updater.

As a precaution against the upgrade not going too well, Update the system before hand, revert from the proprietary video driver to an open source video driver, revert the desktop environment to as default as state as possible. And back up any important data.

Regards

---

### Post by thomas92 on 2016-02-17
Thank you for you answer. And changing 'trusty' to 'wily' in /etc/apt/sources.list and then running sudo apt-get update && sudo apt-get dist-upgrade will work?

---

