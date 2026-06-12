---
title: "Mysteriously changing drive partition ownership"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by cosmolee on 2005-06-07
I'm mounting a DOS partition, /dev/hda1, in /etc/fstab.  I'm using the "owner" option of `mount`, so that the owner of the partition will have write permission and ownership of the file system.  

/etc/fstab:

    /dev/hda1 /home/joe-user/c-drive   vfat    defaults,owner 0       1


I've changed the owner of the partition /dev/hda1 to "joe-user".  However, everytime I reboot, the owner of the partition gets changed back to "root", and only root has permissions on the file system.  

How can I make the owner of the partition persistent, instead of changing back to "root" after reboot?

Thanks.

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=cosmolee]I'm mounting a DOS partition, /dev/hda1, in /etc/fstab.  I'm using the "owner" option of `mount`, so that the owner of the partition will have write permission and ownership of the file system.  

/etc/fstab:

    /dev/hda1 /home/joe-user/c-drive   vfat    defaults,owner 0       1


I've changed the owner of the partition /dev/hda1 to "joe-user".  However, everytime I reboot, the owner of the partition gets changed back to "root", and only root has permissions on the file system.  

How can I make the owner of the partition persistent, instead of changing back to "root" after reboot?

Thanks.[/QUOTE]
 AFAIK, "owner" is RedHat-specific option; it is not available in Ubuntu.
You can easily allow access to this partition for all users (including joe-user) by using umask option:

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

I do not remeber what is the right way to set ownership if you want to have only joe-user and no one else accessing it....

---

### Post by cosmolee on 2005-06-08
The "owner" option is definitely supported in Ubuntu, and is not only for Red Hat. 

I tested this by changing the ownership of the partition to "joe-user", then joe-user was able to mount the partition and the mount point was owned by joe-user, who had full permissions on the mounted file system.  

The problem isn't an issue with `mount`, it is a question of why the owner of "/dev/hda1" keeps reverting back to "root", and how to stop this from happening.

I don't want to use the "umask" or "users" option, because that gives everybody access to the DOS partition.  I only want to give access to a single user.

Cosmo

---

### Post by cosmolee on 2005-06-08
I also looked into using the "group" option of `mount`.  This allows giving multiple users mount capability & access to a file system.  

If I make "joe-user" a member of the group "disk", that will allow him to mount/access any and all drive partitions (which are group "disk").  Obviously, I don't want to do that!

But if I change the group of /dev/hda1 to "joe-user", the same problem exists, in that the group ownership of /dev/hda1 keeps changing back to "disk" after reboot. 

Cosmo

---

