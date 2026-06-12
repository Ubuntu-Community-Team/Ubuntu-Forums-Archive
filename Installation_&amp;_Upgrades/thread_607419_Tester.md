---
title: "Tester"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by testerr on 2007-11-08
I am a new user and am trying to install 7.10 PC version.    I get the following message when I try to instal Apache2    

robert@Telco:/root$ sudo apt-getinstall apache2
sudo: apt-getinstall: command not found
robert@Telco:/root$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache2 has no installation candidate

I am unsure of how to complete this part of installation

---

### Post by ycason on 2007-11-09
sudo apt-get install apache2 
is the command. 

That space in there makes all the difference.:)

---

### Post by rsambuca on 2007-11-09
You need to fix your repositories.  Go to System -> Administration -> Software Sources.  Make sure all of the repositories are checked, and then reload them when prompted.  You should be able to install after that.

---

