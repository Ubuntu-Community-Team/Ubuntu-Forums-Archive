---
title: "updating ubuntu problems"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by dj-toonz on 2006-08-03
hi all, i've just installed dapper drake after using feroda core 5, and having problems trying to update it :(, when i goto do a sudo apt-get update when it get's to the serciuty.ubunbu.com part it freezes for like a couple of mins then comes up with connection timed out, whenever i click on the orange star on the desktop it asks me for the password then come's up with a empty box, no updates appear of nothing, is ubuntu having problems with there servers of what? here's my sources.list and the error log i'm getting

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timedout
Fetched 3453kB in 2m0s (28.8kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.

hope somebody know's as i cant download anything like gnome-art because it connets to sercity.ubuntu.com for some of it's files :-(

---

### Post by markelhas on 2006-10-19
Have the same problem :(, please help.

---

