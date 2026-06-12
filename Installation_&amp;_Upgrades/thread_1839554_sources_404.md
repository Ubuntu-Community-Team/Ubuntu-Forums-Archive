---
title: "sources 404"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by spider_0k on 2011-09-05
I have a Powerbook G4 12". I have installed  Lucid 10.04, including updates without problem.
I am attempting to upgrade to Maverick, online because it is (I thought) straightforward. I am running into this problem. Update Manager fails to update the files in Lucid 10.04. The Internet access is fine but it fails to fetch from repository (404). I haven't changed any setting but since installation. I realized the Update Manager is not working. I tried different servers, cn, tw, us, uk and distributions 10.04, 10,10, 11.04, the results were the same.
Additionally to make things clearer I have simplified my sources.list:-

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe multiverse 
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 

All other internet functions are fine.
Thanks in advance for your help
Philip

---

