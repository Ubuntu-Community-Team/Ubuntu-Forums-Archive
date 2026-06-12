---
title: "Can't complete update"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by VaGentry on 2011-03-31
The update manager recommended seven updates today.  I get an error message when I try to update.  Any suggestions?

Error message reads:

 "installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `linux-headers-2.6.35-24' contains empty filename

---

### Post by dabl on 2011-03-31
Open a terminal.

```
sudo apt-get update
```

```
sudo apt-get -f install
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get clean
```

Post back if you get errors.

---

