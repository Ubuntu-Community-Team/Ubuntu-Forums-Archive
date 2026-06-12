---
title: "Can't upgrade from 9.04 to 9.10"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by dpatel100 on 2011-06-09
I can't seem to upgrade from 9.04 to 9.10. 

I understand it is better to upgrade from one supported release to the next. So I tired to do that using "sudo do-release-upgrade" . I keep getting No New release found. The same things happens in the Update Manager.

pateldil@pateldil-desktop:~[16:38:21]$ sudo apt-get install update-manager-core
[sudo] password for pateldil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


pateldil@pateldil-desktop:~[16:38:29]$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

I have a lot of data that I would like to keep, so I would like to know if there is an easy way to ugprade my Ubunto to more recent versions.

Thanks,
            Dilip Patel

---

### Post by mörgæs on 2011-06-09
Hi, welcome to the fora.

In stead of struggling with upgrading one unsupported release to another I would recommend a fresh install.

Best is to test the new release first in a live boot.

---

