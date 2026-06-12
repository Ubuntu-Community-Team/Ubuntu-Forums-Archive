---
title: "upgrade from 10.10 to 12.04"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by ESimard on 2014-07-02
Hi, I have two machines running ubuntu v10.04 and v10.10.  On the 10.04 machine the upgrade manager offered 12.04 as an upgrade which I did successfully. However on the 10.10 machine the upgrade manager only offers 11.04.  Attempting to run this after the unsupported message the "fetch failed" possible network problem. Net work is fine chrome can connect.  Next I tried do-release-upgrade with the following messages 

   Checking for a new ubuntu release 
    Err Upgrade tool signature                                                    
    404  Not Found [IP: 91.189.92.201 80]                                       
    Err Upgrade tool                                                              
    404  Not Found [IP: 91.189.92.201 80]                                       
    Fetched 0B in 0s (0B/s)                                                       
    WARNING:root:file 'natty.tar.gz.gpg'missing 
    Failed to fetch 
    Fetching the upgrade failed. There maybe a network problem.  

This installation is on a dual boot 32bit machine.  What is the next step to try?
Thanks _Ernie

---

### Post by coffeecat on 2014-07-02
With your 10.10 machine, you would be much better off doing a fresh install of 12.04 or even 14.04, both supported LTS (long term support) releases. 10.10, 11.04 and 11.10 are all end of life and unsupported, and to get to 12.04 from 10.10 you would need to use the old-releases repository described here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

In theory, you could go 10.10 -> 11.04 -> 11.10 -> 12.04 to get to a supported release, but that would take a very long time, involve large downloads and there would be the potential for something going wrong at every step. It would be something I would only attempt as an experiment, not something I would trust on a production system.

Back up your data and re-install fresh with an installation CD/USB prepared with the 12.04.4 ISO would be my advice:

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

**EDIT**: also have a look at the EOL sticky:

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by ESimard on 2014-07-02
Thanks will do a fresh install.
_E

---

