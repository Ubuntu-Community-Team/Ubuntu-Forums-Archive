---
title: "No space left on device after upgrade"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by ddubbz1979 on 2016-08-19
And can't open package manager. I try to update and get messages like "you must manually run sudo dpkg --configure -a to correct the problem. But when I do it can't create or open files on drive e. Any help appreciated. Not sure where to go from here. Everything working fine except for a few error messages and lack of updating.

---

### Post by Bucky Ball on 2016-08-20
Drive E? Do you mean sde? Please tell us more about your setup. Is drive 'E' where you have Ubuntu installed?

You could open a terminal and:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```

You don't need the '-get' for newer releases, e.g. 'sudo apt update' is enough. Please post any and all errors.

---

### Post by Bashing-om on 2016-08-20
ddubbz1979; Hello;

Let's see what is true about " no space left on device" .
Post back - between code tags - the outputs of terminal commands:
```

df -h
df -i

```

we see
[INDENT][INDENT]what tale is told
[/INDENT][/INDENT]

---

