---
title: "[SOLVED] Upgrade from 7.10 to 8.04 - Automatrix"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by BassKozz on 2008-05-24
I am planning on upgrading from 7.10 to 8.04 using the Update Manager soon, but I took a look at the [UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes"):
> Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade. If you have used EasyUbuntu or **Automatix** (neither of which is recommended nor supported), you may have problems upgrading to a newer version that requires a fresh install.
I have Automatrix installed currently; can I uninstall it (uninstall everything it installed and then remove it from Synaptic) and then upgrade and be fine, or will I have to do a "fresh install"?
And if I need to do a "fresh install" how can I backup my settings and replace them after the install is complete?

I am mainly concerned about my VMware settings the most...
Any Idea's?
Thanks,
-BassKozz

---

### Post by Pumalite on 2008-05-24
I you manage to remove Automatix and all other third parties and programs associated with them, you should be fine.

---

### Post by wpshooter on 2008-05-24
I think that I is supposed to be "IF" and IMO, it is a mightly big IF.

My recommendation would be to do a completely new installation of Ubuntu from scratch after you have WIPED your hard drive (assuming that you have nothing on it that you want to keep/save) with [www.killdisk.com](www.killdisk.com).

I think if you try to upgrade after having used this Automatix program, you are NOT going to like the results.

Good luck.

---

### Post by darkmire on 2008-05-24
> **B/-\ssKozz said:**
> I am planning on upgrading from 7.10 to 8.04 using the Update Manager soon, but I took a look at the [UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes"):

I have Automatrix installed currently; can I uninstall it (uninstall everything it installed and then remove it from Synaptic) and then upgrade and be fine, or will I have to do a "fresh install"?
And if I need to do a "fresh install" how can I backup my settings and replace them after the install is complete?

I am mainly concerned about my VMware settings the most...
Any Idea's?
Thanks,
-BassKozz


[COLOR="Navy"]Don't worry too hard about it. Just backup your data and upgrade. I upgraded to 8.04 before I knew about Automatix being discontinued and everything still works. The Ubuntu Upgrade Manager only deselects the repositories Automatix uses and does not remove the packages you installed using it.  (Automatix is just a package manager that installs stuff from repositories that have non-free non-GPL software).   

In fact most Automatix stuff is in the medibuntu repository and all you have to do is put an up to date listing for medibuntu for hardy in your repository lists once the update has finished and that repository will then update in the same way as all your other packages.    Do a Google search under medibuntu for info on how to do this.  

The biggest problem you are most likely to find with a package installed using Automatix is that it ceases to work because the upgrade removes a library that a package depends on.  I personally didn't have a problem with it but if you want to play safe, then don't allow the Update Manager to remove obsolete packages. I actually chose to remove obsolete files and the Upgrade Manager removed Python 2.4 which stopped some stuff working but putting it back solved that one.  

Now VMWare is different.  If it's anything like Virtualbox or Parallels, you will have to update your kernel headers once you have done your Ubuntu upgrade.  The documentation in VMWare will tell you how to do this.  Have a read through before you upgrade Ubuntu.   VMWare is not in any repositories I know of but it is available for download from VMWare when upgrades are available - although I don't know the package well enough to know if this is done automatically or whether you have to check form time to time.  

I hope that helps.  Unless you want to do some hard work, I wouldn't do a fresh install.  The update process produces less glitches as a rule.  You are going to have some work to do even with a smooth install. 
 [/COLOR]

---

### Post by louieb on 2008-05-24
I quite wondering if an upgrade was going to trash my system.  Just before I upgrade I use **partimage **to back up my / and /home partitions.  If the upgrade works the fine. If not I have a quick and easy way to restore my system to working condition.  

When I went from 7.04 to 7.10. I removed Automatrix. but did not remove the programs I had installed with it. Upgrade went fine.

---

