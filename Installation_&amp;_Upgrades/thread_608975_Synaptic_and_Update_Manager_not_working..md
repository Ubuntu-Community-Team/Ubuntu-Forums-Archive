---
title: "Synaptic and Update Manager not working."
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by camiguin on 2007-11-10
When I try to open Synaptic or the Update Manger, both crash with this error message:
E:The package brscan2 needs to be reinstalled, but I can't find an archive for it.
I have the brscan package available, but I cannot reinstall or erase it, either from the console or from adept. Please, help.

---

### Post by kd7swh on 2007-11-10
You should try using apt-get from the terminal to clear up the broken package(s).

```
sudo apt-get update
```

Will update your repos. listing and tell you if you have any packages that you don't need anymore. you may try to use

```
sudo apt-get autoclean
```

to clear the old packages out...

---

