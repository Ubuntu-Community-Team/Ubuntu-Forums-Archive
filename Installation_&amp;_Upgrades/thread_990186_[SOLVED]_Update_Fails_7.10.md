---
title: "[SOLVED] Update Fails 7.10"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Dusenberg on 2008-11-22
Latest update (hp print stuff) fails in either synaptics or console. Here's terminal output:
> root@AVLAPTOP:/home/julian# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  hpijs hplip hplip-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7522kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Fetched 7523kB in 33s (227kB/s)                                                
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)  Size mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@AVLAPTOP:/home/julian# apt-get --fix-missing upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  hpijs hplip hplip-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7522kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB] 
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Fetched 7523kB in 36s (205kB/s)                                                             
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)  Size mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch



Any idea what's wrong. First time I've ever had a problem with an update. :)

---

### Post by Partyboi2 on 2008-11-22
Its a known problem and they are in the process of fixing it.
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247)

---

