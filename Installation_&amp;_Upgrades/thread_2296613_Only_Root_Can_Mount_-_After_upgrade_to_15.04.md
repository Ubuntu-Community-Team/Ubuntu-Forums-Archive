---
title: "Only Root Can Mount - After upgrade to 15.04"
date: 2015-09-27
forum: Installation &amp; Upgrades
---

### Post by DJonsson2008 on 2015-09-27
On my Xubuntu Netbook FSTAB was configured with Ubuntu 14.04 to mount 2 drives on the LAN during boot. 
This worked well for over a year. 

After upgrading to 15.04 though the previous FSTAB method no longer works.

My FSTAB syntax is as follows

//servername/sharname /media/mountname cifs username=me, password=me, iocharset=utf8,sec=ntlm 0 0 

Other Ubuntu (earlier version) machines on the LAN see the LAN drives I'm trying to connect to. 

Was there some change in 15.04 as to how FSTAB works...or does the problem have some other cause.

Any suggestions appreciated.

---

### Post by DJonsson2008 on 2015-09-27
There was a problem on the router, after I rebooted the router and checked all the cables the machine mapped as it should of.

---

