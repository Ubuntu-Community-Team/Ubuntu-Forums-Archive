---
title: "Windows 10 WSL Unable to upgrade Ubuntu 16.04.5 LTS to 18.04.1"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by ket000 on 2018-08-29
I am using Windows 10 Enterprise Version 1709 64 Bit (16299.611) and when starting WSL and trying to run the below command to upgrade to 18.04.1 it fails all the time with network connection error after running for some time

Commands used are

sudo apt update
sudo apt upgrade
sudo do-release-upgrade

I am behind a proxy and I can download other packages and http_proxy and https_proxy variables are set correctly. Not sure why it is failing. 

**Error message is**

Err [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
  Connection timed out [IP: x.x.x.x 80]
Fetched 6,990 kB in 6s (0 B/s)

Error during update

A problem occurred during the update. This is usually some sort of
network problem, please check your network connection and retry.

E:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/bionic/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/bionic/universe/binary-amd64/Packages)
Connection timed out [IP: x.x.x.x 80], E:Some index files failed
to download. They have been ignored, or old ones used instead.


Restoring original system state

Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
=== Command terminated with exit status 1 (Tue Aug 28 15:11:02 2018) ===

---

