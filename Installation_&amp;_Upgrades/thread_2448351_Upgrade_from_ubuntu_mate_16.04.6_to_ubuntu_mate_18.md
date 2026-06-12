---
title: "Upgrade from ubuntu mate 16.04.6 to ubuntu mate 18.04.4 does not work"
date: 2020-08-06
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2020-08-06
Hi,
I finally decided to upgrade from ubuntu mate 16.04.6 64 bit to ubuntu mate 18.04.4 64 bit. I tried as usual with:
```
sudo apt-get update
sudo apt-get dist-upgrade

```

```

sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```
```

sudo do-release-upgrade -d
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```

---

### Post by kc1di on 2020-08-06
[This page]("https://www.cyberciti.biz/faq/how-to-upgrade-ubuntu-16-04-to-18-04-lts-using-terminal/") maybe of help if you want to use the terminal.
or [this i]("https://www.zdnet.com/article/how-to-upgrade-from-ubuntu-linux-16-04-to-18-04/")f you want to use GUI.
Also make sure you backup important files before doing the upgrade. 
Good luck

---

### Post by Impavidus on 2020-08-06
So, what's the output from```
sudo apt-get dist-upgrade
```

---

### Post by erotavlas on 2020-08-06
> **Impavidus said:**
> So, what's the output from```
sudo apt-get dist-upgrade
```

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by erotavlas on 2020-08-10
I found the problem, it was a package with unmet dependencies visible on synaptic, but not on the prompt.

---

