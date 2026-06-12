---
title: "Breezy over Hoary..."
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Elrohir on 2005-10-18
ok, so I just recieved the Breezy Badger cds and I really want to install it... can I install over Hoary without losing any data or messing something up?:(

---

### Post by adwait on 2005-10-18
You would be better of adding cd rom line to the /etc/apt/sources.list and then running apt-get dist-upgrade. For that, put the CD in the drive and run
```
sudo apt-cdrom add
```
after that
```
sudo apt-get update
sudo apt-get dist-upgrade 
```
If something goes wrong
```
sudo apt-get install -f
```
You may have to alternate between these commands, as will be suggested during the upgrade.

---

### Post by Elrohir on 2005-10-18
wish me luck... here I go... :)

---

