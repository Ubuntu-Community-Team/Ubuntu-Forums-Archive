---
title: "Problem with the update manager"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by vig on 2007-09-28
problem with update manager. once i run it it gives the  error " E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

on running in manual - dpkg --configure -a - it says u require superuser priveleges.

Then i went about opening the terminal and typed - sudo apt-get update

it started running but got stuck with the following error - 
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/Release](http://download.tuxfamily.org/syzygy42/dists/feisty/Release)  Unable to find expected entry  exaile-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


well i need help since no update is possible without it

also if i try to run the synaptic package manager from the administrator menu the following error is displayed - 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


pl help

ty

---

### Post by Seisen on 2007-09-28
You just need to add sudo in front of the command so it would look like this.
```
sudo dpkg --configure -a
```

---

