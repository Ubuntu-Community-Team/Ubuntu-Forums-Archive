---
title: "Can't browse NTFS partition."
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by coolen on 2008-09-07
I don't know why, but whenever I try to access my NFTS partition, I'm told I don't have permissions.

I can browse it as root, but not as me.

This is the relevant line in /etc/fstab:

```
UUID=90D47E38D47E2120 /media/xp_pro   ntfs    defaults,umask=007,gid=46 0       1
```

I'm running Intrepid. There were no updates just prior to this. There was an unclean shutdown in Windows, but I did a check and got a clean bill of health.

Any ideas?

---

### Post by Sef on 2008-09-07
Moved to Intrepid Ibex forum.

---

### Post by onero on 2008-09-07
It's probably a permissions problem, not sure if that applies to NTFS drivees though. In any case right-click on your drive and check the permissions. My drive's owner is still root, but has 'Create and Delete files' for Owner, Group, and Others (so full permissions for everyone). Yours probably says samething different. If you want full access for everyone else, you can change the permissions using chmod; alternatively, if you're the only one using the drive, you can just change the owner of the drive using chown. 

You can check how to change permissions in this [thread]("http://ubuntuforums.org/showthread.php?t=445213"). When using these commands, by the way, you can use the -R flag (that means recursive, so the changes will be applied to all sub-folders and files).

---

### Post by zekopeko on 2008-09-07
why don't you try like this

```
/dev/sda1 /media/xp ntfs-3g defaults 0 0
```

of course you can replace the /dev/sda/1 with UUID

---

### Post by coolen on 2008-09-07
I know how to change permissions. Anyway, from Nautilus, I'm told that the permissions could not be determined. The mount point itself has 770 permissions, owner root, group users. chmod seems unable to change the permissions of the mount point (I'm reluctant to use the -R on such a large scale. I once inadvertently made all of the directories in my music folder inaccessible).

I just tried with ntfs-3g. Seemed to work, although using the command outright, group permissions are set to root.

Thank you. I'll see if that works in fstab.

Well, I just tried it using mount -a. Same problem :(

---

### Post by MaX on 2008-09-07
> **coolen said:**
> I know how to change permissions. Anyway, from Nautilus, I'm told that the permissions could not be determined. The mount point itself has 770 permissions, owner root, group users. chmod seems unable to change the permissions of the mount point (I'm reluctant to use the -R on such a large scale. I once inadvertently made all of the directories in my music folder inaccessible).

I just tried with ntfs-3g. Seemed to work, although using the command outright, group permissions are set to root.

Thank you. I'll see if that works in fstab.

Well, I just tried it using mount -a. Same problem :(


I installed disk-manager and had it automatically configure all my NTFS drives. works great now

---

