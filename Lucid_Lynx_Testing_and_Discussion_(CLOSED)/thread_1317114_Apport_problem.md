---
title: "Apport problem ?"
date: 2009-11-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-06
While installing some updates I noticed this...
```
Unpacking replacement python-apport ...
Preparing to replace apport 1.9.3-0ubuntu4 (using .../apport_1.9.4-0ubuntu1_all.deb) ...
stop: Unknown instance: 
Unpacking replacement apport ...
....
Setting up python-apport (1.9.4-0ubuntu1) ...

Setting up apport (1.9.4-0ubuntu1) ...
Installing new version of config file /etc/init/apport.conf ...
Installing new version of config file /etc/default/apport ...
start: Job failed to start
```
Should I generate a new bug report ?

---

### Post by Kevbert on 2009-12-02
After another update today (2nd Dec) apport again fails to start:
```
Setting up apport (1.9.6-0ubuntu1) ...
start: Job failed to start 
```
Looks like apport still faulty (I found out there was a bug with this when I tried to report another bug to the developers!)

---

### Post by SevenMachines on 2009-12-02
if apport is disabled in /etc/default/apport then when the prerm script runs you'll get a job stop warning and when the postinst script runs you'll get job start warning. 
both are non fatal and not a problem, its just a reminder that apport is disabled. if apport is enabled you'll see that the job starts and stops on removal/install fine.

---

