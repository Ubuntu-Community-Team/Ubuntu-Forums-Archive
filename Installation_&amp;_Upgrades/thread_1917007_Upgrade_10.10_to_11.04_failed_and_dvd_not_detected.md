---
title: "Upgrade 10.10 to 11.04 failed and dvd not detected"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by forestman on 2012-01-29
[SIZE=2]hi ppl

I am new ubuntu and i am unable to upgrade from ubuntu 10.10 to 11.04 in my new desk Vostro-260 (Authentication failed. Authenticating the upgrade failed. There may be a problem with the network or with the server), network is OK.

Also. my sys does not detect my DVD Rom and unable to use it for anything, absence of the drive in local and remote disks, no action when i put new or written cd/dvdm, the soft is Brasero Disc Burner.

Thank you for your help[/SIZE]

---

### Post by zvacet on 2012-01-30
From ubuntu software center go to the software repositories and remove all PPA or any other repo you added.Also you can check under server (it usualy say server for...)but you can select find best server.After that

```
sudo apt-get update && sudo apt-get upgrade
```

When you are finish go to the updates manager and try to upgrade.

---

