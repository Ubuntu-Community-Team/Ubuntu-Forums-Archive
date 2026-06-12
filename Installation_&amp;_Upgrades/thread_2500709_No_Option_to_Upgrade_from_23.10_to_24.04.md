---
title: "No Option to Upgrade from 23.10 to 24.04"
date: 2024-09-09
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2024-09-09
I'm running 23.10 and running
>sudo apt dist-upgrade

Gives me
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by Dennis N on 2024-09-09
For upgrade to a new OS version, use **sudo do-release-upgrade**.

---

### Post by guiverc on 2024-09-09
Upgrades using `apt upgrade` or `apt full-upgrade` stay within the same release.

Links that apply are 

- [https://help.ubuntu.com/community/NobleUpgrades](https://help.ubuntu.com/community/NobleUpgrades)

but that no longer exactly applies to your upgrade, as Ubuntu [23.10 is now EOL]("https://fridge.ubuntu.com/2024/07/17/ubuntu-23-10-mantic-minotaur-reached-end-of-life-on-july-11-2024/"); so its more complex as covered in [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by lister171254 on 2024-09-10
Thanks
sudo do-release-upgrade worked despite 23.10 being EOL

---

### Post by ActionParsnip on 2024-09-10
Please mark as solved if all is well

---

