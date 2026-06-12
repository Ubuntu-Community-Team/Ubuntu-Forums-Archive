---
title: "Installing backed up DEB of older versions of Ubuntu"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Xmetalfanx on 2010-01-18
I am wondering if its possible to install older versions of software on newer distro's ... I am on dialup and have a few hundred MB of 9.04 updates and software (including KDe 4 and Xfce)  ... I am wondering if i could (at leaat for the time being install those 9.04 updates on 9.10 .. i still have the cds for both distros and   IF ITS NOT possible or too hard to do, i will go back to 9.04 and when I get to a local High speed access point I will install 9.10 on that other laptap and download the 9.10 updates on that pc, transfering them to this one.   The process of how to "backup" and restore i am clear on .. I have even done it at least once (installing 800MB of downloaded updates, then transfering them to the same ubuntu folder (i honestly forget atm ,... /var/apt/.. something i think) ...   I just noticed that after i tried that with 9.10 many of the packages i have, have updated versions and it wants to get all @800MB all over again ... if i do it with 9.04 .. it says i may need say ... 15MB or something but it detects that the software (800MB) is already there and it doesn't need me to get it again.     thanks in advance for all the help   btw, i am not only asking IF its possible but also how to do it... if its simply a link explaining all of it, i would really appreciate any help

---

### Post by mikewhatever on 2010-01-18
I wouldn't recommend installing 9.04's packages on 9.10. It will, most likely, not work because of differences in versions and dependencies.
If you want to install 9.04's packages on 9.04, copy them to /var/cache/apt/archives and run 
**sudo apt-get update && sudo apt-get upgrade**.

---

