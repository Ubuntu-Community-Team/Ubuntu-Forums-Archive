---
title: "Computer shuts down at 81% install"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by beowulf_lives on 2007-05-17
Hi all,


During installation of Ubuntu 7.04 Desktop Alternate Install the system will power down when the installation is at 81% every time. I don't know which specific package is causing the problem. Does anybody know a work around? I've tried acpi=off

---

### Post by louieb on 2007-05-18
Sounds like a bad burn. Did you run the check media option?

---

### Post by Timokl on 2007-05-18
I had a similar problem with my first install of Ubuntu. You can try this - when you select what kind of installation you would like to have, select "server". This installs a basic ubuntu setup without graphical interface. Then you log in and install the rest through apt-get with:

```
sudo apt-get install ubuntu-desktop
```

It worked with Ubuntu 5.10, I hope it still works.

Bye,
Timo

---

