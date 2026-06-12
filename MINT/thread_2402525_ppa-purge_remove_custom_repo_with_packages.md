---
title: "ppa-purge remove custom repo with packages"
date: 2018-10-01
forum: MINT
---

### Post by ed-lau on 2018-10-01
Tried to use ppa-purge to remove custom repository, e.g. [https://styrion.at/apt/](https://styrion.at/apt/) but did not find a proper way to remove custom repository with installed packages. It is simple to remove repos based on Launchpad or just delete .list file and its key. But remove (downgrade) also installed packages from that repo would be needed.
 Using Ubuntu 18.04 based Linux Mint 19 with MATE desktop, 64-bit.

Repo file content:
```
cat /etc/apt/sources.list.d/styrion.list
deb http://styrion.at/apt/ ./


```

Trials:
```
ppa-purge -s styrion.at 
ppa-purge -s styrion.at apt/ 
ppa-purge -s styrion.at apt/ ./
ppa-purge -s styrion.at -p apt
ppa-purge -s styrion.at ./
ppa-purge ppa:styrion.at/apt/
ppa-purge "deb http://styrion.at/apt/ ./"
ppa-purge -s styrion.at -p "deb http://styrion.at/apt/ ./"
ppa-purge -s styrion.at -p "http://styrion.at/apt/ ./"
ppa-purge -s styrion.at -p http://styrion.at/apt/ ./
ppa-purge -s styrion.at -p /etc/apt/sources.list.d/styrion.list
ppa-purge -s styrion.at -p $(cat /etc/apt/sources.list.d/styrion.list)

```

---

### Post by deadflowr on 2018-10-01
*Thread moved to **MINT***

---

### Post by Frogs Hair on 2018-10-01
It appears the repository isn't a ppa and that's why the ppa-purge might not be working. If the source is removed and this is _not_ a specific application try the following ```
sudo apt auto remove
``` ```
sudo apt update
``` If this repo is in support of one or more installed applications remove/purge the applications and then use the auto remove command. If this repo  has upgraded  many applications it may be better to stay with the packages from the extra repository as reverting could cause broken packages when the applications update from the official repositories.

---

