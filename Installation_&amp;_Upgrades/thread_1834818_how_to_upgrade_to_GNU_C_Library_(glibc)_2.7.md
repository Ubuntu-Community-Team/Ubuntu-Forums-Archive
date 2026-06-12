---
title: "how to upgrade to GNU C Library (glibc) 2.7"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by mhart on 2011-08-28
How do i get glibc upgraded?

sudo apt-get upgrade glibc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
ii  libc6                 2.12.1-0ubuntu10.2    Embedded GNU C Library: Shared libraries

---

### Post by timbaah on 2011-09-06
Did you find a way yet? 

I'm looking for the same information..

---

### Post by montsigur on 2012-08-15
I found the way to do it. You need Synaptic to have it done.
Launch Synaptic -> find glibc -> reinstall
then type: sudo apt-get upgrade glibc
It worked on my Ubuntu 12.04

---

