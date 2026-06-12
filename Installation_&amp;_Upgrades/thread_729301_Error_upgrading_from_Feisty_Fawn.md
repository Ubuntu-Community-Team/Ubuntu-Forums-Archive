---
title: "Error upgrading from Feisty Fawn"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by Roc327 on 2008-03-19
When trying to upgrade to 7.10 using the Update Manager I get an error that reads:


"Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport."



Any suggestions?

---

### Post by Pumalite on 2008-03-19
You might want to try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade
Change the Server to Main if the above doesn't work.

---

### Post by zvacet on 2008-03-19
Is your Feisty up-to-date?

```
sudo apt-get update && sudo apt-get upgrade
```

After this go to the update manager and see if you get message that new version is available.

---

### Post by Roc327 on 2008-03-24
Thanks this worked...now to reinstall/configure my nvidia driver.  Had to do 2nd recommendation first then the first one (thought I had it updated).

---

