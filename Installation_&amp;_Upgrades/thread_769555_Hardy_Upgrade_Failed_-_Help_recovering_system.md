---
title: "Hardy Upgrade Failed - Help recovering system?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Baphijmm on 2008-04-26
Below is the error I got when the upgrade stopped:

Could not install the upgrades
The upgrade aborts now. Your system could be in an unstable state. A recovery will run now (dpkg --configure a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed

Upon restarting, the computer doesn't recognize a file system at all.  fsck died with exit status 8, and it tells me to repair the file system manually.

This has been the worst upgrade experience I've yet had with Ubuntu, and, if I cannot get it back up and running again, I will be forced (but not by much, I'm already 3/4 of the way to doing this already at this point, due to this frustration) to seek out another operating system.  This is ridiculous.

---

### Post by Baphijmm on 2008-04-26
Fixed it by editing /etc/fstab, at least for the time being.  That really shouldn't be necessary though, and it should be something that is either warned about or fixed next time.

---

### Post by dmez01 on 2008-04-30
I'm having a similar problem where it won't finish upgrading and says that my system is in an unstable state. What did you edit in the /etc/fstab file that fixed it?

---

