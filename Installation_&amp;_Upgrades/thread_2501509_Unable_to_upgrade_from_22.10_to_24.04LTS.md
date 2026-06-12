---
title: "Unable to upgrade from 22.10 to 24.04LTS"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by vs-punn on 2024-10-11
I am trying to do the upgrade. When I click on the Upgrade Now button, it starts to download two files, but after that the download window disappears and there is no further action.
Please suggest the solution.

---

### Post by guiverc on 2024-10-11
Ubuntu 22.10 had a single *intended* upgrade path, which was to the next release being Ubuntu 23.04, however that path closed with [Ubuntu 23.04 went EOL]("https://fridge.ubuntu.com/2024/01/26/ubuntu-23-04-lunar-lobster-reached-end-of-life-on-january-25-2024/")

The *official* EOL Upgrades doc is [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) , but be aware you're too late for the *automated *path, so it maybe more work than just backing up data & performing a *clean* install then restoring your data.

Ubuntu 22.04 LTS, or Ubuntu 23.10 have *supported* upgrade paths to 24.04 LTS; ie. *to 24.04* specific upgrade page is [https://help.ubuntu.com/community/NobleUpgrades](https://help.ubuntu.com/community/NobleUpgrades) , where the only upgrade doc mentioning 22.10 is [https://help.ubuntu.com/community/LunarUpgrades](https://help.ubuntu.com/community/LunarUpgrades) (or 23.04 upgrade path).

---

