---
title: "New with upgrade: nfs disks won't unmount, reboot hangs"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by wgscott on 2006-07-07
After upgrading to 6.06, I've had trouble with the reboot sequence.  The biggest problem is when I shutdown or reboot, the system hangs trying to unmount remote disks (nfs and possibly samba).  This did not happen with 5.10 and before. The fstab is the same as before the upgrade.] I have been unable to diagnose the cause. The same thing happens if I issue the command

sudo umount /mymount/point 

(*,)

---

### Post by wgscott on 2006-07-07
anyone?

---

### Post by slavisa on 2006-10-15
same holds for me.

I found out the following:
NFS-Mounts only can't get unmounted, when a gnome-session (didn't test with other Desktop-Environments) was started. Seems to me like a gnome process (maybe nautilus?) still has a lock on the nfs-shares, which confuses me, because gdm and therefore gnome and all related processes are killed during shutdown/reboot.
It wouldn't be a problem if somebody could tell me how to find out which process holds a lock on a certain nfs-mount. Allready tried lsof with no result.
I remember in Debian sarge often the famd (file alteration monitor) holded locks on mounted Filesystems. Killing it was mostly the solution. Which mechanism is used in ubuntu for file-alteration-notification?

have a good night, becuase i will :-)

---

