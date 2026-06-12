---
title: "Failed to install git-email Depends: git (&lt; 1:2.17.0-.)"
date: 2021-02-15
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2021-02-15
Hi,

I am running ubuntu 18.04, my git is in newest version (1:2.17.1-1ubuntu0.5). But why cannot install git-email? 

$ sudo apt install git-email

The following packages have unmet dependencies:
 git-email : Depends: git (< 1:2.17.0-.)

$ sudo apt install git

git is already the newest version (1:2.17.1-1ubuntu0.5).

---

### Post by spjackson on 2021-02-16
It looks like it's trying to install an older version of git-email. Try
```

sudo apt update

```
then re-try the install.

---

