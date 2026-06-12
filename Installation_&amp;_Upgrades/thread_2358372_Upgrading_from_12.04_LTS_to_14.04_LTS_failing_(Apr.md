---
title: "Upgrading from 12.04 LTS to 14.04 LTS failing (Apr 2017)"
date: 2017-04-12
forum: Installation &amp; Upgrades
---

### Post by shoalsart on 2017-04-12
I want to meet the Apr 28 deadline of EOL support for my 12.04 LTS server and upgrade to 14.04 LTS server (as I have another production server running 14.04 LTS efficiently with my current apps). I really don't want a fresh install because of all the apps loaded/configured on server.

I get the message: Your HWE is supported until April 2017" and "New Release 14.04.1 LTS   available".
However when trying to upgrade, I receive "no new release found".

Following the instructions here: [https://help.ubuntu.com/community/UpgradeNotes#From_12.04_LTS_to_14.04_LTS](https://help.ubuntu.com/community/UpgradeNotes#From_12.04_LTS_to_14.04_LTS)
I've attempted to:

  
[LIST]
[*]run sudo do-release upgrade and also tried with both "c" and "d" parameters (knowing d was obsolete now) 
[*]run sudo apt-get dist-upgrade (no issues) 
[*]run sudo apt-get update and sudo apt-get upgrade(no issues) 
[*]checked HWE kernel and updated to Trusty version and also set back to prior generic version (based on a prior bug post about possible kernel upgrade compatibility issue) 
[*]ensured update manager (core) is installed 
[*]/etc/update-manager/release-upgrades file contains:
 [DEFAULT]
 Prompt=lts 
[*]executing from terminal console locally on server 
[*]run:  sudo apt-get install -f and sudo dpkg --configure -a  to check for any broken dependencies. Everything seems fine. 
[/LIST]

Server settings:
[LIST]
[*]Linux 3.13.0-116-generic #163~precise1-Ubuntu SMP x86_64 GNU/Linux 
[*]Distributor Id: Ubuntu Description: Ubuntu 12.04.5 LTS Release: 12.04 Codename: Precise 
[*]   Updated the kernel to 3.13.0-116 (I've tried to upgrade with both 115 and 116 Trusty kernels) 
[/LIST]


Am I missing something simple? I have read where the sources.list file can  be manually edited to Trusty DEB pointers, but this may cause system  issues, any further ideas?

---

### Post by TheFu on 2017-04-13
Beware that many programs have been updated and old config files won't work as intended on the new LTS versions. You'll need to rework all of them anyway.

Seems that you are doing all the expected things. I'd move to a virtual machine and run a number of different test upgrades to learn what goes smoothly and what doesn't.  

During the do-release-upgrade - non-core PPAs/repos are removed. So any programs/packages from PPAs will not be migrated. Many packages have been removed in 14/16.04 releases too.  Definitely need to test before trying all this.

BTW, I'm in the same boat - have 1 system still on 12.04. I've created a new 16.04 VM and have been slowly migrating all the services over.  Have an old RoR webapp that will be the most difficult to move over. The nginx reverse-proxy stuff I'm using needed a few tweaks, but not too much.  I vaguely remember some large changes in apache config files with the move to 2.4.x apache. It wasn't fun figuring those out.

---

### Post by shoalsart on 2017-04-13
Thanks! Yeah I've got one version on a VM platform running smoothly. 

I was also wondering if anyone has tried updating server via .ISO (CD/DVD) route? such as in this thread;
[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

