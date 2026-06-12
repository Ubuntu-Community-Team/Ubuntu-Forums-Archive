---
title: "Aptitude &quot;packages upgraded&quot; wrong?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by Fatman_UK on 2010-10-22
Hi all.

Not sure if I should worry about this. It seems fairly harmless but could indicate corruption of my package database?

```

root@vostro-1:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Resolving dependencies...
...blah...
94 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 251MB of archives. After unpacking 14.8MB will be used.
```

Note, 94 packages upgraded. Aptitude then proceeds to download **103** packages.

Hmm. Worry or not worry?

----

root@vostro-1:~$ dpkg -l | grep aptitude
ii  aptitude                                             0.4.11.11-1ubuntu10                             terminal-based package manager
root@vostro-1:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid
root@vostro-1:~$ uname -a
Linux vostro-1 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

---

