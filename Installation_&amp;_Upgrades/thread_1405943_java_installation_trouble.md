---
title: "java installation trouble"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by selvavicto on 2010-02-13
evening i was installing sun-java6-jdk,at the time due to power problem the installation was broken ,again i was install i got this msg
''
""selva@selva-desktop:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree 
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed
sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
ia32-sun-java6-bin (= 6-15-1) but it is not installable
Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
selva@selva-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?""
i'm a new user 
ple help me.....

---

### Post by zvacet on 2010-02-13
```
sudo apt-get -f install
```

---

