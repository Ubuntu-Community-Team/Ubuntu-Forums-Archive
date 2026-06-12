---
title: "Question on os-uninstaller"
date: 2023-09-07
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-09-07
If I use os-uninstaller, does it remove everything in the Ubuntu partition or does it just remove the enough that there is nothing to boot?  Reason for the question is that I need to recover Evolution message files before trying to get Ubuntu reinstalled.

Thank you,

John

---

### Post by Xian on 2023-09-07
Os-Uninstaller will remove everything on the selected partition -- including the data.

---

### Post by Rubi1200 on 2023-09-08
What is the advantage of this tool over using GParted from the liveUSB to reformat a partition?

If you need to do file recovery you should not be using the drive/partition anyway as any action will overwrite data and lessen the chances of recovery.

Testdisk and PhotoRec might help with recovering data but certainly not a given.

---

### Post by Impavidus on 2023-09-08
If you only want to reinstall Ubuntu, there's no need to uninstall it first. You can simply install it over the current system. If you do this while formatting the partition, it will be a clean install and all data will be wiped. If you don't format, the installer will try to reinstall all packages you had installed earlier and keep your data files. That's the easy option, unless your package manager is messed up.

---

### Post by MAFoElffen on 2023-09-09
Which OS are you uninstalling and what is your goal?

---

