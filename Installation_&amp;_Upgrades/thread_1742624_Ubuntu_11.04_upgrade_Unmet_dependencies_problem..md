---
title: "Ubuntu 11.04 upgrade Unmet dependencies problem."
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Ratnadeep on 2011-04-29
Hello, 
I am trying to upgrade to ubuntu 11.04 from my current 10.10 system.
If i try to upgrade with Upgrade Manager it stops at calculating upgrade step and i can see red circle at top left corner, hovering over this gives message - 

> An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'


If i run 
sudo apt-get dist-upgrade


> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 libappindicator1 : Depends: libdbusmenu-gtk3 but it is not going to be installed
                    Recommends: indicator-application (>= 0.2.93) but it is not going to be installed
 overlay-scrollbar : Depends: liboverlay-scrollbar-0.1-0 but it is not going to be installed
 python-aptdaemon-gtk : Depends: python-aptdaemon.gtk3widgets (= 0.41+bzr646-0ubuntu2) but it is not going to be installed
 python-couchdb : Breaks: desktopcouch (< 1.0) but 0.6.9b-0ubuntu1 is to be installed
 python-desktopcouch-records : Conflicts: desktopcouch (< 1.0.7-0ubuntu2) but 0.6.9b-0ubuntu1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

What might be problem ? i tried googling but couldn't get solution.

---

### Post by dino99 on 2011-04-29
due to new release time, the servers are very busy, try with the "main" server as some mirrors are not fully updated yet

---

### Post by Ratnadeep on 2011-04-29
Yes, i am using Main Servers only, for upgrade. Still doesn't help.

---

### Post by dino99 on 2011-04-29
as it is an upgrade, check your sources.list:

- deactivate everything but genuine natty repo
- clean the sources: sudo rm /var/cache/apt/archives*
- update again

---

### Post by Ratnadeep on 2011-04-29
Hey Dino99,

> - deactivate everything but genuine natty repo

Couldn't get this well, but commented out the some lines and tried but no use. Here is my sources.list file - [https://gist.github.com/947978/51092a2aa8c923b474ba1026aece035873cba25d]("https://gist.github.com/947978/51092a2aa8c923b474ba1026aece035873cba25d")  **(UPDATED..)**

> - clean the sources: sudo rm /var/cache/apt/archives*

Yes, I did this with sudo rm -r /var/cache/apt/archies

> - update again

Same error. I am updating with Update Manager GUI.

---

### Post by el-tarado on 2011-05-04
Same problem here. However, my ```
sudo apt-get dist-upgrade
``` says there are no errors... any clue?

---

