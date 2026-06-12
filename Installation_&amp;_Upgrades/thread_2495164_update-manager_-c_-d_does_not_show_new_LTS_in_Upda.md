---
title: "update-manager -c -d does not show new LTS in Update Manager"
date: 2024-02-09
forum: Installation &amp; Upgrades
---

### Post by erik-martinessanches on 2024-02-09
Updating from 18.04.6 LTS to 20.04.6 LTS by following the [Release Notes]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes"). (Just prior to running update-manager -c -d, I also did apt update and apt upgrade and apt --puge autoremove, if it matters.) They write:

"To upgrade a desktop system:

[LIST]
[*]Open the "Software & Updates" Setting in System Settings.
[*]Select the 3rd Tab called "Updates".
[*]Set the "Notify me of a new Ubuntu version" drop down menu to "For any new version" if you are using 19.10; set it to "For long-term support versions" if you are using 18.04 LTS.
[/LIST]

[LIST]
[*]Press Alt+F2 and type update-manager -c into the command box if you are using 19.10; type update-manager -c -d if you are using 18.04 LTS.
[*]Update Manager should open up and tell you that Ubuntu 20.04 LTS is now available.
[/LIST]
"

The issue is that no new LTS version shows up in Update Manager, even after logout and restart. Update Manager simply says that the system is already up to date.

---

### Post by erik-martinessanches on 2024-02-09
User error, there is indeed an upgrade button in Software Updater!

---

