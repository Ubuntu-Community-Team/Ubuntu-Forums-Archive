---
title: "repository changes"
date: 2021-08-16
forum: Installation &amp; Upgrades
---

### Post by david tutton on 2021-08-16
Hi attempting to upgrade I get the following messages:

det@david-HP-ENVY2:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for det: 
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute-updates InRelease            
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute-backports InRelease [101 kB] 
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hirsute InRelease                    
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security InRelease
Reading package lists... Done
N: Repository 'http://gb.archive.ubuntu.com/ubuntu hirsute-backports InRelease' changed its 'Suite' value from 'hirsute' to 'hirsute-backports'
E: Repository 'http://gb.archive.ubuntu.com/ubuntu hirsute-backports InRelease' changed its default priority for apt_preferences(5) from 500 to 100.
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
det@david-HP-ENVY2:~$ 

This is my release of ubuntu
det@david-HP-ENVY2:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 21.04
Release:	21.04
Codename:	hirsute
I am not sure how to change the suugestions:(

---

### Post by MAFoElffen on 2021-08-16
Submit a bug report to LaunchPad... You have no PPA's in your sources list... Just the standard Repo's.

So somewhere on your machine, there is an, as yet unknown package installed, that needs to be identified. It is not "unkown" as being anything wrong with your system , but rather that there is an updated matching package somewhere in the Repo's that is "unsigned" so APT is giving you a security warning that it is identified as being untrusted...

Launchpad needs to track that package down, so it can be rebuilt correctly and get signed digitally. It is going to take someone there, from comparing your apt logs and reconcile it against the hirsute repo's.

That is what that error is about. After you do that, please post the Bug Report link here, so other's know what that might be and can follow it's progress and if it get's resolved.

---

