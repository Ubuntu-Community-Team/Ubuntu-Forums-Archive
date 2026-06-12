---
title: "Searching for updates?"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by mlvmhn on 2015-07-29
How do i search for new updates using a Terminal command?

I am running Ubuntu 14.04 LTS.

---

### Post by Bashing-om on 2015-07-29
mlvmhn; Hello:
The simple
> 
How do i search for new updates using a Terminal command

response is:
```

sudo apt update

```
Followed by:
```

sudo apt upgrade

```
when updates are available.

[INDENT][INDENT]just that simple and quick
[/INDENT][/INDENT]

---

### Post by mlvmhn on 2015-07-29
Thx. 

What is the upgrade option for? I do not want to upgrade, just update my current 14.04 LTS system. 

14.04 LTS is the latest LTS version right?

---

### Post by howefield on 2015-07-29
> **mlvmhn said:**
> What is the upgrade option for? I do not want to upgrade, just update my current 14.04 LTS system. 

The apt-get update command makes sure that the packaging system is aware of any released updated packages since the last time you ran the command, apt-get upgrade will use that info to update the packages that you have installed in your system. It will only upgrade already installed packages. 

> 14.04 LTS is the latest LTS version right?

Yes, generally every 2 years we get an LTS so the next one is 16.04.

---

### Post by mlvmhn on 2015-07-29
Thx again. How do i install Chrome instead of Chromium? 

I can not seem to find it in Software Center?

---

### Post by howefield on 2015-07-29
> **mlvmhn said:**
> Thx again. How do i install Chrome instead of Chromium? 

I can not seem to find it in Software Center?

You won't find Chrome in the Software Centre, you would need to download the relevant .deb package from the Chrome website. Once downloaded, double clicking the package should be enough to initiate to install process.

---

