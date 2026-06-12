---
title: "upgrading ubuntu"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by reqqq on 2011-07-07
according to this [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
when you Renewing the Installation **without formating** the  partitons (in contrast to upgrading), will also keep the personal data  and configurations under /home but will renew all system settings under  /etc as well as the default set of installed packages

  from the above i understand you can continue use ubuntu after upgrade with all programms installed & everything you have with no problem
my question is when you do the opposite thing ,mean  go etc from 11.04 to 10.10 is possible or you must format ?are there any problems if this is possible with  software installed?
thanks

---

### Post by dino99 on 2011-07-07
if you change the distro name into sources.list, then you just need to update/upgrade to get the new distro, without worrying about your settings as they are under /home:

sudo gedit /etc/apt/sources.list

change each "maverick" by "natty" (its an example indeed)

---

### Post by reqqq on 2011-07-07
> **dino99 said:**
> if you change the distro name into sources.list, then you just need to update/upgrade to get the new distro, without worrying about your settings as they are under /home:

sudo gedit /etc/apt/sources.list

change each "maverick" by "natty" (its an example indeed)

you mean just going and changing in sources list the name natty to maverick and then after updating i have the old distro with no problems? or the above you explain is when you need to just go from 10.10 to 11.04?

---

