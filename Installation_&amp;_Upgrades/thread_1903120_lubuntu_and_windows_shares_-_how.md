---
title: "lubuntu and windows shares - how?"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by mr_si on 2012-01-01
I've got a stock lubuntu install (10.10) however I can't get it to see any XP shares (any network at all tbh).

The explorer window (PCMan) has a go->network drives menu item, this just reports that 'The specified location is not supported' and the address is reported as network:///

The machine has got a samba client installed and for good measure I just installed the full package.

---

### Post by Morbius1 on 2012-01-01
I do not use Lubuntu so I don't know how much help I can be but when something similar happens to Ubuntu or Xubuntu it's usually because there are some packages missing:
```
sudo apt-get install gvfs-backends
``````
sudo apt-get install gvfs-fuse
```

---

### Post by Elfy on 2012-01-01
You might need to logout and login after installing them - I know I had to in xubuntu.

---

### Post by mr_si on 2012-01-02
:D Thanks chaps

---

