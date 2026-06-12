---
title: "Update Manager not showing upgrade to 10.04 anymore"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by hily on 2011-02-05
hey, whenever 10.04 first was available update manager was showing it as available, now even with trying every possible combination of settings in software sources and in the settings menu in update manager, the option to upgrade is not showing up. also tried in the terminal with no updates available as the result...bah.
please help:confused:

---

### Post by dino99 on 2011-02-05
open synaptic, check its repo tab and be sure that the updates boxes are checked (3d tab) (config menu), then update, upgrade

---

### Post by hily on 2011-02-05
i checked the repositories and everything looks good...still no update offered...
any other ideas?

---

### Post by dino99 on 2011-02-05
there are not updates every day, so it depend when you got the last ones. But you still can watch logs to find usefull errors:

- system admin logviewer (/var/log/)
- .xsession-errors (into /home, ctrl+h to unhide)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure update-manager

---

### Post by hily on 2011-02-05
yeah i get that but even if i have 9.10 up to date shouldn't update manager give me the option of upgrading to 10.04?

---

### Post by dino99 on 2011-02-05
> **hily said:**
> yeah i get that but even if i have 9.10 up to date shouldn't update manager give me the option of upgrading to 10.04?

once again, check the synaptic settings

---

### Post by ajgreeny on 2011-02-05
Set the system to do what you want in Software Sources, as others have said.  See Screenshot

---

