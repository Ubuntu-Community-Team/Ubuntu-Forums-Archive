---
title: "Trying to updrade to 11.04 - get error message &quot;Invalid Package Information&quot;"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by askates on 2011-04-28
I currently have Ubuntu 10.10, and I want to upgrade to 11.04. I've been trying to upgrade via the update manager, but I get the message:

"[B]Invalid package information
[/B]After your package information was updated the essential package 'ubuntu-minimal' can not be found anymore. This indicates a serious error, please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.[B]"

[/B]I can upload any of the files, if need be. Someone has already reported an instance of this in the bug report, so I figured I'd ask about it here.

---

### Post by dino99 on 2011-04-28
open synaptic:

- into the repo tab (third parties): unselect ppa, non genuine repo
- check that ubuntu-minimal, ubuntu-desktop, ubuntu-standard are installed

into a terminal:
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

- sudo apt-get update
- sudo apt-get install -f

- sudo gedit /etc/apt/sources.list
 change maverick -> natty
save, update & upgrade

.... this might take a while ...

---

### Post by askates on 2011-04-28
I think I managed to fix it by changing the mirror in sources.list.

---

### Post by dino99 on 2011-04-28
> **askates said:**
> I think I managed to fix it by changing the mirror in sources.list.

yeah set it to "main"

---

