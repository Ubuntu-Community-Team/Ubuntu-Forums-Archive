---
title: "Can't install Virtualbox; &quot;error processing package samsungmfp-driver&quot;"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by Dubbayoo on 2014-06-08
I've recieved an error while trying to upgrade versions of Virtualbox. I was trying to switch to version 4.3.12 and my apt-get install keeps bombing on:

Removing samsungmfp-driver (3.00.90-2) ...
dpkg: error processing package samsungmfp-driver (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 samsungmfp-driver
Error in function: 
------------

I've tried all the following with no change in result:

sudo apt-get install virtualbox-4.3
sudo apt-get install samsungmfp-driver
sudo apt-get -f remove samsungmfp-driver
sudo dpkg -i --force-overwrite /var/cache/apt/archives/samsungmfp-driver_2%3a2_all.deb
sudo apt-get -f install samsungmfp-driver
sudo apt-get clean
sudo dpkg --configure -a


All of these resulted in the same error as before when I try to install virtualbox. Can anyone provide some more insight?

---

### Post by Dubbayoo on 2014-06-08
Solved, edited /var/lib/dpkg/status and removed samsungmfp-driver

---

