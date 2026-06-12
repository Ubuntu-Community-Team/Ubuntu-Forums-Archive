---
title: "Broken  Packages required for upgrade?"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by agarner98 on 2011-03-21
I keep on getting this red " - " icon on my panel and I try to perform the upgrade it prompts me to do. But it says that there are 3 broken packages i need to fix with the "broken filter". How do I fix this so I can upgrade? :KS

---

### Post by zvacet on 2011-03-22
In terminal type

```
sudo apt-get -f install
```

---

### Post by tommcd on 2011-03-22
> **agarner98 said:**
> I keep on getting this red " - " icon on my panel and I try to perform the upgrade it prompts me to do. But it says that there are 3 broken packages i need to fix with the "broken filter". How do I fix this so I can upgrade? :KS
Do you have any third party repositories added to your system? This includes those all to often problematic PPA repos. If you do, and you can not resolve this, then try removing any third party repositories, then run:
```
sudo apt-get update
sudo apt-get-dist-upgrade
```
And see if the upgrades will install.

---

