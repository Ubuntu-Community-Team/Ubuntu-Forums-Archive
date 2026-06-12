---
title: "Update and upgrade and (?) missing files"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by gonzalo-vc on 2016-05-28
Hi, all. I prefer to update/upgrade my *buntu machines using the proper system application (updater). But sometimes I go to the terminal and do it manually, specially to use these 3 commands:
apt-get upgrade --fix-missing
apt-get autoclean
apt-get autoremove

Why is that there are, quite frequently, missing files, libraries, whatever, in ubuntu? :confused:
I think the system updating app must be upgraded to solve this.

---

### Post by TheFu on 2016-05-28
Weekly:
```
sudo apt-get update
sudo apt-get dist-upgrade

```
Monthly:
```
sudo apt-get autoremove
```

Don't know about any GUI tools.  Depending on the specific version of Ubuntu installed, might need to remove old kernels monthly too - easiest way is through **synaptic**, but apt-get can be used too.

---

