---
title: "Failing to download update indexes"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by measdg on 2006-07-30
None of the system updating tools are working for me. I have a new install of Dapper from the CD, and have got internet working okay but none of the methods for updating the system are working.
I have tried: sudo apt-get update;  sudo aptitude update; the Synaptic Package Manager, and the Update Manager. All of these methods fail to download the repository indexes (they time out).

For example:

measdgGLEN-NB01:/etc/apt$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done


I am connected to the internet now, so there doesn't seem to be any problem there, but these tools just don't seem to be able to access the indexes. Any ideas how to resolve this?

I am familiar with linux as a user, but new to setting it up from scratch so please keep that in mind with any help :)

thnx

---

