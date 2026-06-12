---
title: "repos for fiesty upgrade"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by ittiam on 2007-04-10
hey,

am trying to upgrade to fiesty from edgy. But i keep getting some invalid repos during the upgrade..i mean those are active repos but messed up for fiesty upgrade.

can any one give me the exact set of repos required to upgrade to fiesty. i dont want to upgrade from a forsaken repo and get stuck.

---

### Post by zvacet on 2007-04-11
```
  sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

This will change all your Edgy repos to Feisty.

---

### Post by ittiam on 2007-04-12
Yea i did know that. But i didnt want to include any third party repos. Update-manager automatically disables third party repos. So i just wanted to have a list of repos from which fiesty upgrade will go smooth.

---

### Post by zvacet on 2007-04-12
Comment them in your source list(# sign in front of line).When upgrade is finish uncomment.
```
sudo aptitude update
```

---

