---
title: "How to recover from an interrupted upgrade?"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by longbow on 2007-05-08
Last time I tried to updage from 6.10 to 7.04, the upgrade was interrupted when the USB drive where my ubuntu is installed is take off the computer accidentally. 
When I reboot the system, it works fine. However, when I try to doing the upgrade again with
gksu "sh /cdrom/cdromupgrade" (I use cd rom upgrade), the following error occurs. What can I do?:

[COLOR="Blue"]can't load DistUpgradeViewGtk (No module named pygtk)
can't load DistUpgradeViewKDE (No module named qt)

Reading cache

Checking package manager

: 00  
: 100  
Reading package lists: Done

: 00  
Candidate versions: 00  
: 50  
Dependency generation: 50  
Dependency generation: 57  
Dependency generation: 90  
: 00  
: 01  
Reading state information: Done

Reading state information: Done
......
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmp.TzcShU6220/feisty", line 56, in <module>
    app.run()

  File "/tmp/tmp.TzcShU6220/DistUpgradeControler.py", line 1025, in run
    self.fullUpgrade()

  File "/tmp/tmp.TzcShU6220/DistUpgradeControler.py", line 935, in fullUpgrade
    if not self.prepare():

  File "/tmp/tmp.TzcShU6220/DistUpgradeControler.py", line 284, in prepare
    'Yes'

TypeError: askYesNoQuestion() takes exactly 3 arguments (4 given)
[/COLOR]

---

### Post by zvacet on 2007-05-08
This is just suggestion

```
sudo aptitude update && sudo aptitude upgrade
```

If this finish your upgrade replace source list

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

---

