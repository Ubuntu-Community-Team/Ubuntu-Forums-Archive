---
title: "Can't Upgrade to 10.10"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2010-10-21
I have Ubuntu 10.04 and I am trying to upgrade to 10.10 but when I have the update manager check for updates it is not an option.

---

### Post by UnterUn on 2010-10-21
```
sudo apt-get upgrade
``` or
```
sudo aptitude upgrade
```

---

### Post by louis.roux on 2010-10-21
OK I did that and it ran through a few things and said done.  Now what?

---

### Post by sikander3786 on 2010-10-21
Now start update manager. Press Alt + F2 and type

```
update-manager -d
```

Does it list 10.10 now?

---

### Post by UnterUn on 2010-10-21
> **louis.roux said:**
> OK I did that and it ran through a few things and said done.  Now what?
Okay now your up to date on that version (I find that's always useful to do) you should be able to get the new release by doing:
```
sudo apt-get install update-manager-core
```Which will download the core if you don't already have it, then do the update:
```
sudo do-release-upgrade
```EDIT: skiander beat me to it! And i didn't realise you could do it that way....:)

---

### Post by louis.roux on 2010-10-21
got it guys. thanks

---

