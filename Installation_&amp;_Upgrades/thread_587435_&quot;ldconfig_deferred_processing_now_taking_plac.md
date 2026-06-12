---
title: "&quot;ldconfig deferred processing now taking place&quot; does not end"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by ericcart on 2007-10-22
I upgraded from festy to gutsy.

Now, when I install something, the installer ends with "ldconfig deferred processing now taking place".... and never ends !!!

So I kill gksu to recover.....


**I reproduced it installing/uninstalling for ex. Kopete. I think It's somewhat related with "Apps/Add/Remove" (WRONG) vs "System/Administration/Synaptic" (OK).**

I can install and uninstall Kopete with System/Administration/Synaptic, but not with Apps/Add/Remove without ldconfig hung.



Is this a BUG ? What is happening ? Is there any way to recover from it ?

I think everytime a I kill ldconfig the system deteriorates.


Thanks
Eric

---

### Post by ericcart on 2007-10-22
I opened the bug:

gnome-app-install - "ldconfig deferred processing now taking place" does not end
[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041)

Thanks,
Eric

---

