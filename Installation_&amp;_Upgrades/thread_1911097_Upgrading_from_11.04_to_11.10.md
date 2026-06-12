---
title: "Upgrading from 11.04 to 11.10"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by buzkill on 2012-01-18
It seems that I'm unable to update from 11.04 to 11.10
I've been receiving an error about missing ubuntu-minimal, so i've uninstalled it, and then re-installed them.
After it still didn't work I attempted to do it through terminal:


sudo apt-get install update-manager-core
is reported to be up to date, but
"sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found"

While it does show up in update manager..

Thank You.

---

### Post by cortman on 2012-01-18
> **buzkill said:**
> It seems that I'm unable to update from 11.04 to 11.10
I've been receiving an error about missing ubuntu-minimal, so i've uninstalled it, and then re-installed them.
After it still didn't work I attempted to do it through terminal:


sudo apt-get install update-manager-core
is reported to be up to date, but
"sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found"

While it does show up in update manager..

Thank You.

Try

```
sudo apt-get update && dist-upgrade
```

---

### Post by buzkill on 2012-01-18
Behind firewall atm, so can't get most of the files, but i do get
"dist-upgrade: command not found" message

---

### Post by raja.genupula on 2012-01-18
> **buzkill said:**
> It seems that I'm unable to update from 11.04 to 11.10
I've been receiving an error about missing ubuntu-minimal, so i've uninstalled it, and then re-installed them.
After it still didn't work I attempted to do it through terminal:


sudo apt-get install update-manager-core
is reported to be up to date, but
"sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found"

While it does show up in update manager..

Thank You.
do you got any errors while doing this , i mean
```
sudo apt-get update
```

 if not then do this in terminal 
```
do-release-upgrade
``` 
let me know what you got :):)

---

### Post by buzkill on 2012-01-18
> **raja.genupula said:**
> do you got any errors while doing this , i mean
```
sudo apt-get update
```

 if not then do this in terminal 
```
do-release-upgrade
``` 
let me know what you got :):)

Well first one still returned that there are no new upgrades, but the second one worked (it seems) thank you. :D

Will report in a few hours if it finishes installing/ downloading without any new hiccups =)

Edit:
And everything updated perfectly. Thank You, gain :)

---

