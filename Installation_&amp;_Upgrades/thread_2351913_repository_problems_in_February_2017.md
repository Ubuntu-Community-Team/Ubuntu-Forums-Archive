---
title: "repository problems in February 2017"
date: 2017-02-07
forum: Installation &amp; Upgrades
---

### Post by bobmounger on 2017-02-07
I am running 16.04 on a dell laptop, & can see the internet. update is slower than I have ever seen it. After 10 minutes this is as far as the command has gotten

xxx:~$ sudo apt-get update
[sudo] password for x: 
Hit:1 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                                               
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]                               
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]                                       
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [463 kB]                               
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [455 kB]                   
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [306 kB]                    
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [194 kB]                           
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [133 kB]                           
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [162 kB]                                  
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]                        
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]                                   
0% [Connecting to security.ubuntu.com (2001:67c:1560:8001::14)]                                                                         


What have I done to this machine?

---

### Post by QIII on 2017-02-07
Probably nothing.

Repos slow down when being updated, when there are throughput issues between you and them, etc.

The first thing to do is try again in an hour or so.

If that does not work, switch to a different mirror.

---

