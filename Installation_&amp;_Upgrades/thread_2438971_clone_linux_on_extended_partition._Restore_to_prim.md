---
title: "clone linux on extended partition. Restore to primary partition?"
date: 2020-03-20
forum: Installation &amp; Upgrades
---

### Post by link626 on 2020-03-20
I've never done cloning before.

16.04 is currently installed on an extended partition.

I want to clone this partition to an image. 
in case the drive fails, I want to restore this image to a **primary **partition.

Is this done easily? Does it matter what kind of partition the original linux was installed on?

---

### Post by oldfred on 2020-03-20
Partition UUID will be different if not restored to same partition without reformatting.
UUID is used by grub to boot, fstab to mount partitions and maybe in a few other places. You would have to manually edit all of those.

Most of use assume we will just reinstall Ubuntu. No need to backup something that is free and easy to install.
Then we restore our data (mostly /home), installed applications from backed up list and maybe some settings from /etc if you manually edit any system settings. I edit so few, I just copy those files into /home so backed up.
I also prefer to keep /home inside / and have a large data partition which I separately backup.

Many threads on backup and many alternatives. Most use rsync or rdiff or combinations there of.
Some seem to want image backups, but those are obsolete as soon as you start using system.

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc)

If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

