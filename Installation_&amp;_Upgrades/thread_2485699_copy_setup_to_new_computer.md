---
title: "copy setup to new computer"
date: 2023-04-06
forum: Installation &amp; Upgrades
---

### Post by matrooswolf on 2023-04-06
Hi, 

I'm thinking of buying a new computer as I'm switching jobs and have to hand in my old computer. What would be the easiest way to copy my old setup + data (on a separate home partition) to the new computer.

I'm running ubuntu 22.04.2 on a HP Probook intel core i5 8GB 256 ssd now, and would be moving to a Lenovo Ryzen 7 16GB 512 ssd.

Any advice at what would be the easiest way to do that?
Thanks!

---

### Post by TheFu on 2023-04-06
> **matrooswolf said:**
> Hi, 

I'm thinking of buying a new computer as I'm switching jobs and have to hand in my old computer. What would be the easiest way to copy my old setup + data (on a separate home partition) to the new computer.

I'm running ubuntu 22.04.2 on a HP Probook intel core i5 8GB 256 ssd now, and would be moving to a Lenovo Ryzen 7 16GB 512 ssd.

Any advice at what would be the easiest way to do that?
Thanks!

It depends on how you setup your computer(s).  If you are a typical end user and keep everything in your HOME directory, then you only need to backup that and a list of installed packages (put that list into a text file). Done and done.  If you have gone crazy customizing settings outside your HOME directory, then you'll need to get those customized config and data files (don't bother getting programs or libraries).

Easiest:
Pull the HDD/SSD and install it into the new system. Before pulling the storage, disable proprietary GPU drivers.  Since this is "work", you are probably violating company policy if you take any data, equipment, etc.

Next Easiest:
Use the normal backup/restore method you've been using.  Backup everything in your HOME and restore it on the new computer to your HOME there.

If you don't have a backup method already setup, get one.  Which is best depends on how much data is involved and the type of data.  For example, huge media files should use rsync.  Normal user settings and documents would use a real versioned, backup tool and as long as you are going through this effort, best to spend an hour to set it up so you can do it on the next computer running.  

We need to work backwards for what we need to ensure we grab all those things.
**Restore**
[Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) - Steps to restore file-based backups
With the proposed, file-based, method below, as long as the files are placed into the correct directory with the correct owner, group, permissions, ACLs, etc, then it doesn't matter if the underlying storage massively changed.  We can go from ext4 to ZFS or BTRFS or xfs. It doesn't matter.

**A simple backup command:**
[Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329) - be certain to read the caveats. For example, the backup target storage must be native linux, not MS-Windows (no NTFS, no FAT32, no exFAT).
```

# This assumes backup storage is using a native linux filesystem and mounted to /Backups.

# Get lists of installed packages - automatically installed and manual - we can use this at restore time to feed back into APT
/usr/bin/apt-mark showauto |sudo tee /root/apt-mark.auto
/usr/bin/apt-mark showmanual |sudo tee /root/apt-mark.manual

# backup selected areas and safe-to-backup file types only.
sudo  /usr/bin/rdiff-backup
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --include /usr/local --include /etc  --include /root  --include /home \
        --exclude '**'   /       /Backups/

# Remove really old backup sets - say 90 days old.
sudo /usr/bin/rdiff-backup --force --remove-older-than 90D    /Backups/$(hostname)

```
Will get all the data that most end-users would need.  Mainly, their HOME directory.  /root and /etc/ and /usr/local/ should be tiny, so why not grab them?  They do have very useful information.  We put the list of installed packages into /root/ since that might be sensitive information.  

**Storage Used?**
The last command prevents retaining too many backups.  As posted, it keeps 90 days of versioned backups.  This will take about 1.3x the storage that the source files require. If you have 10G in source files, then 90 days of daily versioned backups would use about 13G.  Seems like a bargain to me.  

**How Long?**
The first backup will take as long as it takes to copy all the data.  But all the following backups will only take as long as the changed data requires to store.  It is significantly faster than rsync.  Usually, 1-3 minutes are needed per system, per day, to perform a backup.  You can automate it or run it and go get coffee from the office machine around the corner. When you come back, it will be completely.

The latest rdiff-backup version will always appear like a mirror, so to restore files, we can use cp, rsync, rdiff-backup, or just a file manager.  But at restore time, we need to ensure the correct owner, group, permissions, ACLs and xattrs are retained. If they aren't, we can end up with useless data that doesn't work.  OTOH, for a typical end-user with all the files in their HOME, the owner and group will probably be their userid and groupid.  There are only a few files that require exact permissions - for example, ~/.ssh/ and all the files inside it must have correct permissions or ssh, sftp, scp, and any other libssh-based tools will refuse to work.

---

