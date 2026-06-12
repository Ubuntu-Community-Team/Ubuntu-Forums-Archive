---
title: "freecontrib.org problems? Try alternate upgrade method"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by gvgerman on 2006-10-28
I've found other users herein who, like me, have had problems with freecontrib.org when trying to upgrade. 

See: 
[http://www.ubuntuforums.org/showpost.php?p=1674990&postcount=9]("http://www.ubuntuforums.org/showpost.php?p=1674990&postcount=9")
[www.ubuntuforums.org/showthread.php?t=286176"]http://www.ubuntuforums.org/showthread.php?t=286176]("http://[/INDENT)

Using the "alternate install" method found at [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades"), I was able to circumvent the freecontrib.org problem and successfully upgrade to Ubuntu 6.10.   

Note: When using the alternate install method, the upgrade manager will ask if you want to check the web for the latest packages. I had to select "no" since the upgrade manager failed when freecontrib.org yet again failed to respond.  If you select "no", all the packages will be upgraded from the alternate CD.

The alternate CD image that is used for the upgrade is available from the [download sites]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download").

---

### Post by apocalypso on 2006-10-28
Okay, I'll try this one out tomorrow morning, since I'm in fact having trouble with the freecontrib.org issue.
These are the actual errors I'm getting:
```
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg No pude resolver 'packages.freecontrib.org'
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz No pude resolver 'packages.freecontrib.org'
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz No pude resolver 'packages.freecontrib.org'
```

Hope to have this sorted, I'll let you know! :-k

---

### Post by gvgerman on 2006-10-28
If all goes well, after you have Edgy running, go to:

System > Administration > Software Sources 

and deselect the Alt Install CD.  Three things happened for me:

Synaptic reloaded
Many more programs were available from the repositories
Additional package updates became available from the package manager

I hope this works for you.

---

### Post by itismike on 2007-01-28
Correct me if I'm wrong, but one developer decides to stop hosting a repository and now upgrades fail?  Surely someone has a workaround for this (other than downloading the .iso).  This type of single-source dependency can quickly damage the robustness of the Linux community.

---

