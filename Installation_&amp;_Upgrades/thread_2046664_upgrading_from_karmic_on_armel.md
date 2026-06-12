---
title: "upgrading from karmic on armel"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by warren3000 on 2012-08-23
Hi

Upgrading an armel cpu based device from karmic using:

sudo apt-get install update-manager-core 
sudo do-release-upgrade -d

Results in:
Updating repository information
WARNING: Failed to read mirror file
Done downloading            
Done downloading            
Done downloading            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-armel/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-armel/Packages.gz) 
404 Not Found [IP: 91.189.91.28 80] 
, W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-armel/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-armel/Packages.gz) 
404 Not Found [IP: 91.189.91.28 80] 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting

It turn out
[http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-armel](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-armel)
does not exist.
 
There is no usable GUI, solution will need to be command line based. 
apt-get update and apt-get dist-update worked file using old-release archive.

Thanks

---

### Post by mörgæs on 2012-08-23
Upgrading 9.10 to 12.04 is quite a step. You are likely to get a better result with less effort by doing a fresh install.

---

### Post by warren3000 on 2012-08-23
Issues with that too.

[http://ubuntuforums.org/showthread.php?p=12186124#post12186124](http://ubuntuforums.org/showthread.php?p=12186124#post12186124)

and to lucid will be fine, 10.04

---

### Post by 5l4y3r on 2012-08-23
> **mörgæs said:**
> Upgrading 9.10 to 12.04 is quite a step. You are likely to get a better result with less effort by doing a fresh install.

I agree. Such upgrades are usually problematic, specially when you have a partition with Windows.

---

