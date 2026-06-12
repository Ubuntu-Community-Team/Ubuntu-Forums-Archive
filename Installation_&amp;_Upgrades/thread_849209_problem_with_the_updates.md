---
title: "problem with the updates?"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by amirfaisal on 2008-07-04
Hello..

first of all i just want to say i'm kind of new to ubuntu..
because of that i am having a problem which i find very hard to resolve.
when i click on the icon showing how many updates are available, i am unable to update...
when i press install updates in the update manager to install the updates, i will get this message..


An error occured

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.




i hope someone can can help me out here..coz i really dont no what to do..

---

### Post by lisati on 2008-07-04
Open up a terminal (on the Applications->Accessories menu), and type: 
```
sudo dpkg --configure -a
```

You will be asked for your password, which will be invisible while you type it. 
When this command has finished, try the updates again.

---

