---
title: "Ubuntu 7.10 Online Upgrade Stopped Halfway"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by KevKesh on 2008-01-13
Hi i installed Ubuntu 7.04 using Wubi and dual boot with Windows XP. After update my Ubuntu 7.04 I decided to upgrade to Ubuntu 7.10. After downloads the package and installing I saw open office failed to install only open office give the error message..

After that, when the installation reach 80% the installation process jus disappeared. But, my Ubuntu version is 7.10. After restart the panels look a bit different then it came back to old style and I even got an error message saying that "failed to initialize HAL'

The network icon on panel also shows no network connection but there is Interent connection actually. Its kinda a bit messed up after upgrade.

Anyone, please tell me what is going on.

---

### Post by zvacet on 2008-01-13
```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

If that doesn´t help try 

```
sudo apt-get dist-upgrade
```

and post errors here(if any).

---

### Post by PmDematagoda on 2008-01-13
You can also try:-
```
sudo dpkg --configure -a
```

---

