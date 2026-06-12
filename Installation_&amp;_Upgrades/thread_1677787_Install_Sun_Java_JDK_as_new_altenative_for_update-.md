---
title: "Install Sun Java JDK as new altenative for update-java-alternative"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by lykeion on 2011-01-29
You should install Sun JDK with the package manager. To aAdd Partner repository, update and install:
```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

