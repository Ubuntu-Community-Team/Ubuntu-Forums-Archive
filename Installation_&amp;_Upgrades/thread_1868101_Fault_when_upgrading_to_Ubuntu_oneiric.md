---
title: "Fault when upgrading to Ubuntu oneiric"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by patdundee on 2011-10-23
Not sure if i am in the right place here but I am sure someone will tell me :)
 
I upgraded my server from 10.10 to 11.10 and then it upgraded again to oneiric. Since This has happened a couple of stragne things have happened

1) Every so often after a reboot it fails to load the network and I have to edit the file and re save it and reboot. I then have to go through all the apt update etc and redod the sources list

2) When the upgrade occured i lost recent updates to sites and scripts were missing.  So i re did the site scripts and uploaded them

3) Web sites keep appearing back as they were before the upgrade and the replacement scripts and then on a reboot they revert back to the most recent scripts.

Example A joomla site suddenly comes up with errors and will not load, after one or 2 reboots it reverts back and loads correctly. It is almost as if there are 2 copies of the site and as I rectify the network and redod the APT update / upgrade it keeps changing
 
I have tried the fix out for the network but it still looses it every so often
 
Fix below
[FONT=Courier New]mv /var/run/* /run[/FONT]
[FONT=Courier New]rmdir /var/run[/FONT]
ln -s /run /var/run
ln -s /run/lock /var/lock
REBOOT
apt-get update
apt-get upgrade
apt-get clean all
 
Any ideas people 
 
Thanks

---

