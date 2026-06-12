---
title: "Massive failure upgrading Lucid to Precise"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by jdsmofo on 2012-12-15
I did some searching but did not find anything like my problem.  I was running Kubuntu 10.04 that was updated, with some third-party PPAs.  Everything was working fine, but decided to upgrade to 12.04, given that support for 10.04 would not last much longer.  At a terminal, I typed "sudo do-release-upgrade".  It started downloading, and then installing.  It said that there were errors, and now I have no networking.  My version claims that it is still Lucid.  However, since knetwork now no longer works (I get: "KNetworkManager cannot start because the installation is misconfigured....") , I cannot do much of anything else. 
It is not easy to give any more details because I now have to type these error messages in by hand to another computer.

Since I have no connectivity, I cannot upload any logs or error reports.  Neither can I reproduce the error messages that came with trying to upgrade.

I would be willing to try a fresh install, but would need some direction since I have a fully encrypted hard drive, LVM, separate home directory partition, etc.  

Any help is appreciated.

---

### Post by zvacet on 2012-12-17
If packages are downloaded and started to install try with

```
sudo apt-get -f install
sudo dpkg --configure -a
```

Maybe these commands resolve your problem.

---

