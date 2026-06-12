---
title: "webserver - disable release upgrades"
date: 2020-10-21
forum: Installation &amp; Upgrades
---

### Post by clusterix on 2020-10-21
Ubuntu 18.04.5 LTS


I have a webserver installation with 18.04 and would like to keep it for now
I have already set release upgrades to "never" in:


/etc/update-manager/release-upgrades
Prompt=never


however, it seems to be ignored and the following is planned to be installed during an update:
ubuntu-release-upgrader-core
python3-distupgrade


can these packages safely installed if i want to keep 18.04 LTS, or should I uninstall both:
ubuntu-release-upgrader-core
python3-distupgrade

---

### Post by Impavidus on 2020-10-21
They can be safely installed.

The software for the release upgrades is installed, even when prompting for release upgrades is disabled. That means that you can simply change a setting if you want to upgrade later.

---

