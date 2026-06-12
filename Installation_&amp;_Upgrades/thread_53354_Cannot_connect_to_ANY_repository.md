---
title: "Cannot connect to ANY repository"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by gordonbp on 2005-07-31
I cannot connect to ANY repository AT ALL. My first suspicions were aroused when on install, (and this has happened twice with Hoary and one with Kubuntu) it takes at LEAST 20 minutes to get past the "configuring APT" section.

If I do "sudo apt-get update" I get the following:
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (1.0.0.0), connection timed out

This happens whatever I try to do. 
A second question - should it say (1.0.0.0) or should that be a proper IP address and if so, WHY is it sayong 1.0.0.0?

How on earth do I correct this? I'm getting very frustrated at not being able to update packages and install new ones because i can't connect to ANY repository! (ADSL.......)

---

### Post by gordonbp on 2005-07-31
Fixed - added ISP DNS server to resolv.conf

---

