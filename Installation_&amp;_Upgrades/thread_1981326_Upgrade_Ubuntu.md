---
title: "Upgrade Ubuntu"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by Danijel Dzojic on 2012-05-16
Hey all,i have Ubuntu 10.04 and if there any option to upgrade Ubuntu to 12.04 ? Or is only one option and that option is to down and up operating system?

---

### Post by cmont899 on 2012-05-16
you can do the following:

```
sudo apt-get dist-upgrade
```

may have been changed to 

```
sudo apt-get full-upgrade
```

---

### Post by darkod on 2012-05-16
Yes and no.

Since you are running the previous LTS, the option to upgrade to 12.04 LTS will appear in Update Manager only after the first .1 is released, in other words 12.04.1. That is scheduled for July.

So, you can wait until July and do the upgrade then. Some issues noticed in 12.04 should be repaired in 12.04.1 and in theory it should be better.

If you don't want to wait, open terminal and start the update manager with the -d option, that will make it show the upgrade button for 12.04:

sudo update-manager -d

---

