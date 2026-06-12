---
title: "Re-installation while preserving files?"
date: 2017-12-14
forum: Installation &amp; Upgrades
---

### Post by sterator on 2017-12-14
It's my understanding that one can do a clean install of Ubuntu in such a way that doesn't overwrite data files...Can anyone offer suggestions for making this go properly?

I have an install of 17.04 which has some kind of issue I can't resolve. One solution seems to be to re-install over the top, but I don't want to lose data files. If I lose preferences, so be it.

Thank you for any tips!

---

### Post by oldfred on 2017-12-14
Always, Always have good backups.

But you can do a "dirty" install. Only files that are part of distribution including all the default system wide settings in /etc will be overwritten. So if you manually changed settings like grub, NFS, fstab or others, they will be overwritten. I normally copy any /etc system file I manually edit into /home so my normal backup of /home includes those files without having to backup all of /etc. 
Best to use same userID and password.

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by sterator on 2017-12-14
OK.. I do have a backup on another drive. I would back up the main drive but I can't get in..some kind of booting problem I don't know how to fix.

will this "dirty install" put ubuntu back the way it was originally? or close to it?

will it properly install it?  I can use same user/password

thank you

---

### Post by sterator on 2017-12-14
or should I simply do a fresh "new" install as though the first time?

if so, can I set up the drive to protect me from system fails?

---

### Post by leunam12 on 2017-12-15
Better to rsync /home to another drive, re-install from scratch and rsync /home back to Ubuntu drive ```
sudo rsync -aAXPv /home /path/to/backup/device
``` then, after re-installation (keep same user name and password)```
 sudo rsync -aAXPv /path/to/backup/device/home/ /home/
```

---

### Post by ian-weisser on 2017-12-15
You should probably explain this "booting problem".
Maybe a reinstall will fix it, maybe not.

---

### Post by oldfred on 2017-12-15
Reinstall and restore from backup is normally the last resort after trying to resolve issues.
Sometimes just reinstalling grub2's boot loader or full uninstall/reinstall of boot loader.
But it also can be hardware issues, which should be investigated before just reinstalling. Log files may give info, if drive can be mounted.

---

### Post by sterator on 2017-12-15
> **leunam12 said:**
> Better to rsync /home to another drive, re-install from scratch and rsync /home back to Ubuntu drive ```
sudo rsync -aAXPv /home /path/to/backup/device
``` then, after re-installation (keep same user name and password)```
 sudo rsync -aAXPv /path/to/backup/device/home/ /home/
```


Are you saying that, to get my rsync-backed up documents back into my Documents folder on the boot volume, that I need to rsync them back over, rather than dragging them?

I did re-install Ubunt 17.04 last night, then installed the little updaters, then allowed the 17.10 upgrade to happen.

I installed the handful of mission-critical applications that I need and I have essentially a pristine installation of 17.10, sans files.

---

