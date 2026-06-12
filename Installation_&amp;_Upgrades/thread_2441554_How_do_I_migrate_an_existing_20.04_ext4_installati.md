---
title: "How do I migrate an existing 20.04 ext4 installation to zfs root on different disk?"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by jdrch on 2020-04-24
I have a 20.04 ext4 installation (successful upgrade from 19.10!) and am just wondering about the above. 

One caveat I can think of is [HTML]/etc/fstab[/HTML] and some other things may be somewhat different for ZFS root and so should probably not be transferred over. Is there any way to automagically avoid/resolve such conflicts, or should I just do a clean ZFS root installation and setup from scratch?

---

### Post by scorp123 on 2020-08-27
> **jdrch said:**
> I have a 20.04 ext4 installation (successful upgrade from 19.10!) and am just wondering about the above. 

One caveat I can think of is [HTML]/etc/fstab[/HTML] and some other things may be somewhat different for ZFS root and so should probably not be transferred over. Is there any way to automagically avoid/resolve such conflicts, or should I just do a clean ZFS root installation and setup from scratch?

I'd definitely recommend a clean reinstallation, there will be too many headaches otherwise. You could make a backup of your /home where all your personal files and settings are (e.g. onto a USB harddrive), reinstall the system with ZFS, then carefully copy back the files in your backup into your new /home folder. That way you'd keep your settings and your files and it should not have any negative side-effects on the system.

Also worth saving could be e.g. /etc/ssh in case you have your current system's SSH keys stored there. Just copy them away.  After reinstallation you can copy back your original /etc/ssh/* files and that way your system's SSH keys wouldn't even change. 

With the right preparation (taking a backup of /home ...) you could be done with all this in like 1 hour with little to no headaches.

---

### Post by TheFu on 2020-08-27
Beware:
ZFS isn't production ready for use as an OS or boot partition.  
ZFS is 100% production ready for data, however.

If you choose to go this way, thanks for testing it!  Please open bugs for any issues you find.  Make certain you have backups for anything too important to lose.

---

