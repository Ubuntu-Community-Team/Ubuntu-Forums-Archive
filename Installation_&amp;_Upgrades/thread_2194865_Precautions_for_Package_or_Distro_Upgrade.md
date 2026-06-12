---
title: "Precautions for Package or Distro Upgrade"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by solution.wand on 2013-12-21
Hello Ubuntu Community, 
I am new to Ubuntu and using Ubuntu Server ( Command Line ) for LAMP Development. I am using Ubuntu Server 12.04 LTS on VM at local network. 
I am used to check updates and upgrades most of time. I have few question. 

I am sure that linux is very flexible and reliable in upgrades but just for good practice:

1. Should we backup something before some "upgrade" is available in case of **Package Upgrades** or** Distro Upgrades**? Detailed guidance shall be quiet useful for a learner like me. 

I am concerned because I don't want to lose my data or settings during any upgrade.

---

### Post by ian-weisser on 2013-12-21
Yes. If using a VM, and you have the disk space available, take a snapshot before upgrading. 
You should backup regularly regardless of upgrades.

In my 9 years of Ubuntu, minor upgrades and release upgrades have led to no data loss at all.
Several hardware failures, thefts, admin mistakes, and other non-upgrade causes have led to merely minor data loss...because we had backups to restore from.

---

