---
title: "Upgrade from Dapper won't happen"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by rebelxt on 2008-05-21
I have a completely up-to-date Dapper Drake system and want to upgrade to, eventually, Hardy Heron.  My understanding is that I have to go to Edgy Eft first.

Alt-F2 gives a "Run Application" window, into which I type:

           gksu "update-manager -c" 

check "Run in terminal", and click the Run button.  After entering my password, the resulting 'Software Updates' window says "Your system is up-to-date".  The terminal window has this warning: "apt API not stable yet".  Nothing gets updated.

Help!?!

---

### Post by logos34 on 2008-05-21
no, you can upgrade from one LTS to the next.  

gksu "update-manager"

(if it refuses again, you might try getting the Hardy **alternate** install cd and upgrading directly from disc)

Dapper --> Hardy:
[https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197](https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197)

---

