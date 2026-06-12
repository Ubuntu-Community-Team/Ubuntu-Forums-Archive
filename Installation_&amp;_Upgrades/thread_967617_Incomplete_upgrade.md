---
title: "Incomplete upgrade"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by JGT on 2008-11-02
Hi

I'm getting some strange stuff after my upgrade.

I can't open Software Sources in the menus any more.

Installing from apt gives me:

[PHP]john@john-desktop:~$ sudo apt-get install kde-nightly
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kde-nightly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde-nightly has no installation candidate[/PHP]

Installing new software from Synaptic gives me "449 packages will be held back and not upgraded".

I think the upgrade is incomplete. Can I reapply the upgrade somehow?

Thanks

John

---

### Post by JGT on 2008-11-02
Bump

---

### Post by Pumalite on 2008-11-02
Try:
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by JGT on 2008-11-02
Thanks - it's downloading the packages now. I'll let you know if it's worked in...5h 40s!

John

---

### Post by JGT on 2008-11-03
Thanks - it worked.

John

---

### Post by feng85jie on 2008-11-03
[Air Filter](http://www.chinafengjie.com/air-filter/)Ruian Fengjie Auto parts manufacture CO.,LTD is a company specilized in Filter and Filter components service.

---

