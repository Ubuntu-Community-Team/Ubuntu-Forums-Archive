---
title: "System disk damaged"
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by DaveK6 on 2013-12-20
My server crashed due to hard disk errors. While the disk is still partially readable when mounted in a docking station, it is no longer usable. 

The problem is when I try and reinstall Ubuntu Server 12.04 onto a new disk and then restore backups of data and some configuration files via BackupPC I have discovered that the numeric ownerships no longer match thus generating access issues galore.This problem may be due to the fact that the  server was initially  8.04, then upgraded to 10.4 and finally 12.4; the new server was a fresh install with users and groups being created in a different order and metapackages being installed in a different order, thus generating different numeric IDs.

While I don't have a complete backup of the system disk, I do have /etc and /home on the backup and access to much of the old system when the bad disk is mounted in a docking station.

Any suggestions for how to get the server up and running quickly and recover files properly?
TIA,
Dave

---

### Post by tfrue on 2013-12-21
I would run 'fsck' on the old drive to check for errors, and possible re-install 12.04 on the new disk, and don't overwrite and configuration files from 8.04 to 12.04. I don't think you will need any of the files off the /etc directory, but maybe the /home directories if you saved any files that are user specific there that won't change the config files of the new server.

---

### Post by DaveK6 on 2013-12-21
I did the fsck and the error count continues to grow...

How can I have configuration files on the new (empty) disk BEFORE reinstalling 12.04?

---

### Post by ubfan1 on 2013-12-21
Try to copy  the /etc/passwd and /etc/group files off the damaged disk.  Those contain the user/group ids assigned on the old system.  You can manually make the new system match them to avoid some problems in the restore.

---

### Post by tfrue on 2013-12-22
I was lead to believe that you were copying the files from an older installation to the newer one and that is why you were getting ownership errors and possibly other errors,> The problem is when I try and reinstall Ubuntu Server 12.04 onto a new  disk and then restore backups of data and some configuration files via  BackupPC I have discovered that the numeric ownerships no longer match  thus generating access issues galore.This problem may be due to the fact  that the  server was initially  8.04, then upgraded to 10.4 and finally  12.4; the new server was a fresh install with users and groups being  created in a different order and metapackages being installed in a  different order, thus generating different numeric IDs. Then I'm unsure of what you're trying to do.

Chris

---

### Post by DaveK6 on 2013-12-22
I have an existing 12.04 system on a damaged disk that had been upgraded in place from 8.04 to 10.04 to 12.04, backups on a removable disk, data files on a separate LVM array, and a brand new disk that I did a virgin install of 12.04. When doing the virgin install I selected several metapackages (Mail server, Database server, etc.) that created users and groups. After the installation I then added backuppc which likely ended up with a different numeric user ID and led to ownership issues.

Based on other suggestions I'm likely going to try and install the most basic server possible, recover /etc/passwd, /etc/group, and /etc/shadow from the damaged drive, next manually try and add the various metapackages and then - hopefully - be able to reinstall anything else from the backups.

Dave

> **chris_johnson2 said:**
> I was lead to believe that you were copying the files from an older installation to the newer one and that is why you were getting ownership errors and possibly other errors, Then I'm unsure of what you're trying to do.

Chris

---

### Post by tfrue on 2013-12-22
Good luck! Hope all goes well.

Chris

---

