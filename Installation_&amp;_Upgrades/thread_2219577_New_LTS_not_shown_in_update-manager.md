---
title: "New LTS not shown in update-manager"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by hvn2 on 2014-04-24
Hi,

Running 12.04 LTS, I want to upgrade straight to 14.04 LTS. My settings are as such, but no upgrade is shown. When I change it to any new version, 12.10 is shown. Setting back to new LTS only, only 12.10 is shown. Is this straight upgrade from LTS to LTS not possible ?

Thanks

---

### Post by slickymaster on 2014-04-24
Just run the following in a terminal window:```
sudo apt-get update && sudo apt-get upgrade

```After that done run```
sudo update-manager -d
```When prompted, enter your user password. The Update Manager application will open after a few seconds with a prompt to upgrade. Click this button to begin the process.

---

### Post by hvn2 on 2014-04-24
Thanks. That did it.

---

### Post by slickymaster on 2014-04-24
You're welcome, just glad you got it working.

---

