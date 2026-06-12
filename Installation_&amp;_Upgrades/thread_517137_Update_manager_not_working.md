---
title: "Update manager not working"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by Filip Popovic on 2007-08-04
Hey,

i am new Ubuntu user, after an initial satisfaction I ran into the following problem.

I cannot run any setup of the program because the update manager is always working:(

Moreover, I cannot run update manager as well:(


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks a lot.

---

### Post by Alexander2007 on 2007-08-04
> **Filip Popovic said:**
> Hey,

i am new Ubuntu user, after an initial satisfaction I ran into the following problem.

I cannot run any setup of the program because the update manager is always working:(

Moreover, I cannot run update manager as well:(


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks a lot.

Open a terminal window and type: ```
sudo dpkg --configure -a
``` and Synaptic should fix itself.

---

### Post by Filip Popovic on 2007-08-04
More problems occurred after I used the given command in terminal window.

If I run, update manager, i get the following response:

'The error message: BrokenCount >0'

If I run Synaptic manager, it says I am using a different program.

So I am stuck.

Thanks.

---

### Post by Alexander2007 on 2007-08-04
> **Filip Popovic said:**
> More problems occurred after I used the given command in terminal window.

If I run, update manager, i get the following response:

'The error message: BrokenCount >0'

If I run Synaptic manager, it says I am using a different program.

So I am stuck.

Thanks.

Did you try restarting?
After restarting open a terminal window and type: ```
sudo dpkg -P contacts
``` then ```
sudo apt-get update dist-upgrade 
```
Hope it works.

---

