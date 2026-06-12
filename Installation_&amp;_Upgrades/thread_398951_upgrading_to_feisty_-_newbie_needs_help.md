---
title: "upgrading to feisty - newbie needs help"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by mpooley on 2007-04-01
hi
I intend to upgrade from edgy eft as soon as feisty is gold.
but i havnt got a clue how ?

when i do it will i lose any of my old setup? should i backup my data?

---

### Post by Majorix on 2007-04-01
```
sudo apt-get dist-upgrade
```

will do. And no, you won't lose anything. Your files will stay as-is and the programs will be updated to newer versions.

---

### Post by mpooley on 2007-04-02
> **Majorix said:**
> ```
sudo apt-get dist-upgrade
```

will do. And no, you won't lose anything. Your files will stay as-is and the programs will be updated to newer versions.


ooh great!!:)

---

### Post by zvacet on 2007-04-02
[https://help.ubuntu.com/community/FeistyUpgrades]("https://help.ubuntu.com/community/FeistyUpgrades")

---

### Post by miggols99 on 2007-04-02
I think you put this into the terminal
```
gksudo "upgrade-manager -c -d"
```
It's supposed to be safer than apt-get dist-upgrade.

---

### Post by mpooley on 2007-04-02
> **miggols99 said:**
> I think you put this into the terminal
```
gksudo "upgrade-manager -c -d"
```
It's supposed to be safer than apt-get dist-upgrade.

TA!:)

---

