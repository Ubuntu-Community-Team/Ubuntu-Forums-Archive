---
title: "Strange update error"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2012-07-08
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/planet76.com_repositories_._en, E:The package lists or status file could not be parsed or opened.'


I hope one of the gurus of Ubuntu can explain this message and what to do about it.

Thank you,

John

---

### Post by drs305 on 2012-07-08
Threre is a problem with one of your package lists. You can clear the lists files via the terminal. Be very careful to run the commands exactly as posted since you are deleting files as root:
```
sudo rm -vf /var/lib/apt/lists/*
sudo rm -vf /var/lib/apt/lists/partial/* 
sudo apt-get clean  && sudo apt-get update
```

The lists will be recreated when you run the update command.

---

