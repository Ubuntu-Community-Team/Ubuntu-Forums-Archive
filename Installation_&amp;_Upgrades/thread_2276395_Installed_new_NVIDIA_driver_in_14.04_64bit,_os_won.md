---
title: "Installed new NVIDIA driver in 14.04 64bit, os wont boot now"
date: 2015-05-02
forum: Installation &amp; Upgrades
---

### Post by fandfpcsupport on 2015-05-02
Hello, I have a 64 bit version of trusty on a 1TB drive, and I installed a new NVIDIA 64 bit driver, and when I rebooted It didnt load the os.  I have 32 bit trusty on another drive on the pc, and can load and run that os, and access the other drive containing the broken 64 bit os, how can I fix? (revert the old driver and repair the damage?).I have been customizing the 64 bit version for many months and really want to save it if at all possible.  Thank you in advance.

---

### Post by kc1di on 2015-05-02
Do you know which driver you had previously that worked?  
Simply boot to in the recovery mode. 
It will bring yo to a page that has several options:  first click on the network setup line.  let it finish making a connection. of course this all depends on you having a Ethernet connection.  Then once it is connected click on  root teminal line.  It will take you to a root prompt.  from there you should be able to do the following:
```
apt-get purge nvidia
```
```
apt-get install nvidia-xxx
``` (XXX being the number of the nvidia driver that worked for you) (on mine it is nvidia-304)
or your can install the nouveau driver (open source) if that worked for you in the past. 

Good luck :)

---

