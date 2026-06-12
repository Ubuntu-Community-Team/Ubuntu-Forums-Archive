---
title: "error occurred while RUNNING UPDATE MANAGER"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by AKHOURI on 2011-01-12
i am new to ubuntu and it was working fine till few hours ago..

update manger is showing following error message

----------------------------------------------------------

COULD NOT INITIALIZE THE PACKAGE INFORMATION


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

-----------------------------------
PLZ HELP...:(

---

### Post by Rubi1200 on 2011-01-12
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal and run these commands:

```
sudo rm /var/lib/apt/lists/* -vf
```
```
 sudo apt-get update
```

Hopefully, this will sort it out.

---

### Post by hansolo4949 on 2011-01-12
You should also run sudo apt-get upgrade.

---

### Post by DrPeter_Kille on 2011-01-22
I have experienced the same error with update manager on Ubuntu 10.10 and tried many of the other posted solutions but hansolo4949 fix was the only one that worked....

Many Thanks   :D

---

