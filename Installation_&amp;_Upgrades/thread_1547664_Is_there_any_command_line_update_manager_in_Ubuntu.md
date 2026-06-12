---
title: "Is there any command line update manager in Ubuntu?"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2010-08-07
Hi,

Is there any command line update manager in Ubuntu? Please tell.

Please help.


Thanks,

Vivek

---

### Post by kostkon on 2010-08-07
Give:
```
sudo apt-get update
```
to check for updates
and:
```
sudo apt-get upgrade
```
to install them.
or as one command:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mikewhatever on 2010-08-07
Aptitude is a whole lot more then just an update manager. It's pretty much a CLI equivalent of the Synaptic package manager. That said, if all you are looking for is updating the system, aptitude is probably an overkill.

---

### Post by v1ad on 2010-08-07
to search

apt-cache search file_name

---

