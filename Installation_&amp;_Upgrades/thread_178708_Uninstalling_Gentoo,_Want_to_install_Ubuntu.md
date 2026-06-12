---
title: "Uninstalling Gentoo, Want to install Ubuntu"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by Zombithium on 2006-05-18
Hi,

I recently changed my motherboard from Asus A7N266-Vm to A7V400-MX. I am not able to get Gentoo working (the X server particularly) for the new motherboard (actually haven't tried hard enough). 
But then I want to try Ubuntu now. For that I want to uninstall Gentoo (i have a pretty old release on Kernel 2.4, that's another reason why I want to uninstall). 
Any ideas where to start with this uninstallation procedure?

Thanks.

---

### Post by skirkpatrick on 2006-05-18
When you install Ubuntu, it will ask you which drive/partition you want to use.  You can tell it to use your Gentoo partition and to just delete what's already there.

---

### Post by Sef on 2006-05-18
> But then I want to try Ubuntu now. For that I want to uninstall Gentoo (i have a pretty old release on Kernel 2.4, that's another reason why I want to uninstall).
Any ideas where to start with this uninstallation procedure?

First download the Ubuntu Live CD and make sure you can boot up ok.  If you have any problems with the live cd then very likely you will have problems with the install cd.  

If all goes well, then when you use the partitioner in Ubuntu either use the default which will take over the whole disk or if you do a manual partition, delete the Gentoo partition or partitions first.  Then reinstall them.  If you have any problems with the install cd partitioner, delete all of the partitions with the live cd.  Then reinstall them with the install cd.  All should go fine.

---

### Post by Zombithium on 2006-05-18
Thanks! that helps.
I'll start right over.

---

