---
title: "Unable to upgrade Hardy heron 8.04"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by SecretScarabina on 2008-08-03
Hello 
I'm quite new to Ubuntu , and am having a problem trying to upgrade .
Whenever I try to use the update manager I get a message saying that it is unable to get exclusive lock.

I've tried sudo apt-get purge / clean / install  for the apt-get , and the same for aptitude.
 
All I get when I try this is the following message - 
E:Could not get lock /var/lib/dpkg/lock - open ( 11 resource temporarily unavailable )
E: Unable to lock the administrative directory ( var/lib/dpkg) , is another package running ?

As far as I know , no other package is running the update manager 

Any help would be very much appreciated

---

### Post by Pumalite on 2008-08-03
Close Synaptic or other apt-get processes

---

