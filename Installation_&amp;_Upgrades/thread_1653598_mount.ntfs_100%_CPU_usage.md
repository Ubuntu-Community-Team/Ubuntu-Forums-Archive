---
title: "mount.ntfs 100% CPU usage"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by trancephorm on 2010-12-27
Recently, I noticed mount.ntfs process is eating complete CPU power. I think it came with newest update. I use fully updated 10.04, and having some SMB shares mounted to /mnt ...

Anyone else is having the similar problem?

---

### Post by juxtaposer on 2011-01-06
Yes. Noticed recently when virtual machines mounted on the NTFS side of the same disk started stalling. System Monitor shows mount.ntfs eating 100% even while the system is idle. If this is confirmed recent can we roll back ntfs-3g or what?

---

### Post by mnik11 on 2011-01-30
I have the same issue with ubuntu 10.04 (Linux 2.6.32-28-generic #55-Ubuntu SMP).

The mount point for the external USB HD (Western Digital) frequently goes to 100% CPU usage at which point the only remedy seems to be to kill the mount process and then do umount + mount of the drive. This is very annoying as I can't do this when I am not local to the PC (no remote access to the box).

Does anyone have a better solution, I am sick of kill+umount+mount? 

Thanks

mnik

---

### Post by mnik11 on 2011-02-12
I have a suspicion that use of rsnapshot and/or rsync may have something to do with this issue. I use rsync for backup/mirroring over LAN and rsnapshot for same-disk (USB attached) snapshots. 

Are you by any chance using any of these on regular basis? Also, are you aware of any bugtraq tickets for this issue?

mnik

---

### Post by mnik11 on 2011-02-21
Just to report - after removing rsnapshot from the cron schedule I don't have any CPU utilisation issues. 

I am not sure why the exact relationship with rsnapshot but one of the things that may be causing or contributing to the issue was that the NTFS volume in question had nested directories which forced rsnapshot to create directories above (what I think) is the NTFS limit (8 levels). This in turn created file system problems (i.e. inaccessible folders) - even check disk on Windows 7 did not manage to repair fully these sub-folders.

mnik

---

### Post by dmik on 2011-03-09
Just to report too. I've been annoyed by this problem for many months so finally I gave up and did some digging.

Thanks to the following command (executed when the problem shows up):
```

sudo lsof <path_to_NTFS_mount>

```

I easily found that the 100% CPU load is created by the updatedb.mlocate script run by cron once per day to update the locate database (man updatedb for more info).

For some reason, updatedb.mlocate thinks that all directories on the NTFS partition have been changed and performs a full rescan of the partition which creates high CPU load due to the limitation of the free version of the ntfs-3g driver used in Ubuntu (this limitation is well known and described somewhere else).

A possible workaround is to append the path to the NTFS mount point to the PRUNEPATHS variable in /etc/updatedb.conf to exclude this mount point from the process of updating the locate database.

The fact that updatedb.mlocale thinks all directories on an NTFS partition are always new is probably related to the way how inodes are represented by ntfs-3g. It's just a guess -- I haven't looked into details; if someone does and has a solution preventing full rescanning on each run, I would like to hear it here as this would be a more correct solution than excluding the whole mount point from updating.

---

### Post by mnik11 on 2011-03-09
dmik

Good post - it's a shame I cannot verify if my system was suffering from the same cron script or not. It would be just too painful to re-start rsnapshot.

Since I don't have the CPU issue since I switched off rsnapshot I think the lowest common denominator could be the limitation of the free ntfs-3g driver in ubuntu which you mention. I was always under impression rsnapshot was very intensive in terms of I/O load (even with low percentage of file changes on the volume) so I guess it was probably hitting the ntfs driver limits. 

All the best
mnik

---

### Post by dmik on 2011-03-09
mnik11, Thx.

Yes, it looks like everyone may be having a different application that hits this ntfs-3g limit in a given setup but all of them should be easy to spot with the use of 'lsof' (need to note again that it must be run as root because such applications are usually system-wide daemons). I hope this information will help others. This problem was driving me mad every other morning :)

---

### Post by forza.stiinta on 2011-09-24
Is there any fix for this? I am having this issue in 11.4 ...

---

### Post by Gralgrathor on 2012-03-15
> **forza.stiinta said:**
> Is there any fix for this? I am having this issue in 11.4 ...

No. Basically, NTFS support for linux is rubbish. Available drivers cause extreme CPU usage. I understand that CPU usage increases exponentially with fragmentation of files. This would be consistent with my own experiences: I am running a couple of VM's on an NTFS volume. The virtual disks are stored in single file volumes which can grow to up to 64G in size. Lately my elitebook has started sounding like a geriatric vacuum cleaner. Unfortunately I want to keep the volume NTFS so that I can easily switch my VM images to a windows box if necessary, so moving to EXT4 is not really an option. You'll just have to learn to live with it, or find an excuse to drop NTFS altogether.

---

