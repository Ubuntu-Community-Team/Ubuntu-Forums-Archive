---
title: "software index is broken"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by masmithrpg on 2011-10-14
i've had this for a while, but i need to get it resolved now so that i can upgrade to 11.10.  

The message i'm getting is 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

if i run sudo dpkg --configure -a i get 

dpkg: error: parsing file '/var/lib/dpkg/updates/0023' near line 0:
 EOF after field name `all.png'

if i run sudo apt-get update it runs for a while then fails with 
Fetched 2,744 B in 16s (165 B/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

if i run sudo apt-get install -f i get 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

any ideas on how to fix this 

thanks 

mike

---

