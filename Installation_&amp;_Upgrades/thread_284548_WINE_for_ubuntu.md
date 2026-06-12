---
title: "WINE for ubuntu"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by Dark_Dragon on 2006-10-25
Hey all, i must b gettign to b rather a nucence here :S sorry if i am, im wondering if there is a set version of wine for ubuntu... i have a few diff versions of wine for linux but the package files are not compatable with ubuntu. If there is is there a link for it for D/L or do i need to b connected to the net to get it?

thanks,

-- DD

---

### Post by at0mic on 2006-10-25
First, add repository for Wine: 
gksudo gedit /etc/apt/sources.list
Add the following lines at the end of this file 
# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
Save the edited file 
sudo apt-get update
sudo apt-get install wine

u should read the wiki entirely. it will save u from asking questions and feeling guilty. eg = search wine

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by NetworkGuy on 2006-10-25
Installing wine from the automatix2 package should also get you up and running.

---

### Post by Dark_Dragon on 2006-10-25
so it can only be installed by beeing connected to the ineternet then?

---

