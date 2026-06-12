---
title: "After synaptic completetion"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by tawee2008 on 2008-02-18
Dear Ubuntu fans,

I found this pop-up message after I have installed something from synaptic:
"E: mysql-server-5.0: subprocess post-installation script returned error exit status 1"
What should I do? and what does it mean? 
Perhaps, recently I uninstalled mysql and reinstall mysql, not sure wheter it is concern or not.

Thanks

---

### Post by zvacet on 2008-02-19
```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f install
```

---

### Post by tawee2008 on 2008-02-19
first code doesn't show anything. But, second code show as below:
".... Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0"

Still, don't have any idea!:confused:

If looking into services, it enables 3 mysql servers; mysql, mysql-ndb, mysql-mdm :confused:...

---

### Post by Partyboi2 on 2008-02-19
Try removing it and its config files
```
sudo apt-get remove --purge mysql-server
```
then install it again
```
sudo apt-get install mysql-server
```

---

