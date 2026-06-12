---
title: "upgrading to feisty"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by truth_forum on 2007-04-08
need help please. i tried to upgrade from dapper LTS drake to feisty using the instructions: below is the entry: 
 
 gksu "update-manager -c"

(gksu:5354): Gdk-WARNING **: locale not supported by Xlib

(gksu:5354): Gdk-WARNING **: cannot set locale modifiers
(update-manager:5355): Gdk-WARNING **: locale not supported by Xlib

(update-manager:5355): Gdk-WARNING **: cannot set locale modifiers
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

(synaptic:5365): Gdk-WARNING **: locale not supported by Xlib

(synaptic:5365): Gdk-WARNING **: cannot set locale modifiers:


what is wrong or missing here? 

thanks and more power!   

truth seeker 1

---

### Post by flossgeek on 2007-04-08
You can't upgrade from Dapper straight to Feisty. It would upgrade to edgy. In most cases you are better off doing a fresh install. Feisty is still in Beta you might want to consider waiting before it is officially released.

---

### Post by truth_forum on 2007-04-09
thanks for the information. at any rate, what was wrong with the output considering that i used the official update. it should have upgraded to the next stable release, edgy.

---

### Post by zvacet on 2007-04-09
Maybe you should update Dapper before upgrade.
```
sudo aptitude update
```

If this doesn´t help try 
```
sudo aptitude upgrade
```

and then upgrade to Edgy.

---

### Post by truth_forum on 2007-04-14
i tried the following: 

sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



what is OB? 


thanks

---

### Post by flossgeek on 2007-04-14
0 bytes

---

### Post by truth_forum on 2007-04-18
then what should i do next if i got OB? 
thanks. sorry really dont know much about linu really trying to upgrade to edgy.. thanks..

---

### Post by Voland on 2007-04-18
You got 0 bytes to download because you tried to download updates for dapper. To use edgy mirrors you can change "dapper" string to "edgy" in /etc/apt/sources.list but this is not "real" Ubuntu way. As flossgeek said, just try fresh install or update with Edgy CD/DVD.

---

### Post by truth_forum on 2007-04-19
ok. thanks. i guess their still bugs with the update manager in dapper when upgrading to edgy, i will try to fresh install.

---

