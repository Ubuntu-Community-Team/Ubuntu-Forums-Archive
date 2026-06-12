---
title: "upgrade from 12.04.5&gt;14.04.5&gt;16.04.01"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by exm1110b on 2016-11-13
hi..
i'm attempting to do a non interactive upgrade from ubuntu 12 to 16. 

now doing the first upgrade goes well, however after i reboot and do a the 2nd upgrade (sudo do-release-upgrade -f DistUpgradeViewNonInteractive)  it hangs in the question of keeping the "issue" file, i can press Ctrl+C to exit the process, but i can't redo the upgrade off course. 

if i try to do an interactive upgrade it works, naturally i have to change the references in our scripts  from eth0 to ens32 otherwise i won't have any network. 


the reason i have to upgrade such a lengthy process is because the first ubuntu os is created via an automated process for creating Virtual Machines, and such a process does not support more advanced versions. so i'm forced to use this

---

