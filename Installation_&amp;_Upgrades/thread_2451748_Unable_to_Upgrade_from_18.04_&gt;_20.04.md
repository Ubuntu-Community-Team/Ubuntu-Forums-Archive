---
title: "Unable to Upgrade from 18.04 &gt; 20.04"
date: 2020-10-10
forum: Installation &amp; Upgrades
---

### Post by vanquishvictor on 2020-10-10
Hi All,

Trying to upgrade my Ubuntu laptop from 18.04 > 20.04

First is gave me the option in software updater > select upgrade > No change

I then tried through terminal but I get: Please install all available updates for your release before upgrading.

So I ran **sudo apt update && sudo apt upgrade , **but got the following error

The following packages have been kept back:
  wine-stable
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.

Any information / workaround around would be appreciated

Please note that I am following this article: [https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

---

### Post by rsteinmetz70112 on 2020-10-10
If a package is "Held Back" you can often clear it by simply installing it again.

```
sudo apt install wine-stable
```

You may need to add --reinstall option

---

### Post by CelticWarrior on 2020-11-22
Try removing the Wine PPA.

---

### Post by CelticWarrior on 2020-11-22
The main problem is the third-party software sources (for release upgrades), not so much what was installed from them.
Again, check Software & Updates > Other software. Remove the PPA there.

If you want you may uninstall it as well with the usual command
```
sudo apt remove wine-stable
```

---

