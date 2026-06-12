---
title: "ubuntu with Oracle 11g"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by froghead on 2010-03-24
Hi,
 
I am new to Linux. I would like to use Ubuntu to learn and play around with Oracle 11g Rel 2. 
 
I am currently running Win 64 bit with Oracle 10g Rel 2.
 
I have a Tyan n3600b board with 2 Opteron CPU's and 16GB of RAM. The machine has been running well for 8 months now.
 
I am simply looking for some direction as to the following:
1. flavour of Ubuntu to consider; i.e. amd64 bit desktop or Ubuntu 9.10 Server
2. Or should I consider Ubuntu at all, since Oracle only supports Red Hat and their own flavour of Unix.
 
Any suggestions would be most appreciated.

---

### Post by lemming465 on 2010-03-28
Dual CPU with 16 GiB RAM is certainly enough to play with a DB on.
> 1. flavour of Ubuntu to consider; i.e. amd64 bit desktop or Ubuntu 9.10 Server
With 16 GiB RAM I'd definitely go with amd64 rather i386; databases strongly prefer directly addressable memory, and performance will likely be around 20% better on a DB workload.  Server versus desktop is a matter of taste; the base OS and package repositories are the same either way, it's just a matter of whether you are planning to do command line stuff (server style) or GUI stuff (desktop style).  If you sit at a directly connected keyboard and screen, as seems likely, I'd suggest desktop.  Note that oracle installers are written in Java, so the install likes to be GUI anyway.

> 2. Or should I consider Ubuntu at all, since Oracle only supports Red Hat and their own flavour of Unix.
Oracle's Linux flavor is a little like CentOS, it's basically cloned off the RedHat enterprise source RPM's.  Oracle also directly supports SuSE.  I haven't tried installing Oracle 11 on anything, much less Ubuntu, so I'm not sure what issues you might run into.  An LTS release such as Ubuntu 8.04 which has been out for more than 8 months is likely to be less work to run Oracle on than something bleeding edge like Lucid beta 1.

---

### Post by 123ghouse on 2011-02-03
Hi 
I am new to Ubuntu
I installed Ubuntu 10.10 in my PC of 32 bit
Can you help me in installing oracle 11g in my ubuntu 10.10

---

