---
title: "Fast Q About Upgrading to Lubuntu 18.04"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2018-04-27
So, I just downloaded Lubuntu 18.04 and successfully did an encrypted install on an old X40 "test system."

Is there a way of painlessly upgrading my existing encrypted Lubuntu 16.04.1 systems to 18.04?

When I use this sequence on one of them, 

sudo apt update && sudo apt dist-upgrade && sudo apt autoremove
sudo apt-get install update-manager-core
sudo nano /etc/update-manager/release-upgrades
sudo do-release-upgrade –d  

The last command tells me that no upgrade is available. Is this because the Lubuntu upgrade sequence is not yet available, or is there a separate method for Lubuntu (as opposed to Ubuntu)?

Thanks!

Bill

---

### Post by Bashing-om on 2018-04-27
wjbmd48; Hello;

Yeah. the LTS upgrade path will not be opened up until the  .1 release.
see: [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Upgrading_from_Ubuntu_16.04_LTS_or_17.10](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Upgrading_from_Ubuntu_16.04_LTS_or_17.10)

[INDENT]just the way it is
[/INDENT]

---

### Post by wjbmd48 on 2018-04-27
Thanks!!

I'll wait,

Bill

---

