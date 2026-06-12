---
title: "restarted with the time urgrade"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by hanishjadala on 2012-01-12
[ATTACH]210736[/ATTACH]hey everyone ive restarted my pc when it was upgrading from 11.04 to 11.10 and it got crashed and i am unable to get into the ui i can able to get the command mode when i select the recovery mode. but unable to view the normal start up of the system.i am getting an error i am adding as attachment...
help me out...

---

### Post by lemming465 on 2012-01-21
If it got interrupted part way through an upgrade, things are in a confused state, where components that are supposed to match don't, e.g. new binaries might be looking for shared libraries which are not yet installed or old binaries might be looking for ones no longer installed.   You can probably fix this by using command line tools to try to complete the upgrade.  Do the recovery mode boot and log in.  Then try something along the lines of:```
sudo -i
apt-get install aptitude
aptitude update
aptitude full-upgrade
apt-get -f upgrade
dpkg-reconfigure -a
```

If that doesn't do it, plan B might be to do an overlay style re-install using version 11.10 media, but without reformatting any disk partitions.  This would keep your data files, e.g. home directory stuff.

---

