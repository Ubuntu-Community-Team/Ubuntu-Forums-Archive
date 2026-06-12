---
title: "Can I install Ubuntu 16.04.02 as ext3 instead of ext4?"
date: 2017-03-22
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2017-03-22
I'm running Windows 7 and Ubuntu 16.04.02 on the same hard drive.

A third partition, formatted NTFS, stores data from both operating systems.

When I installed Ubuntu, it automatically formatted its partition as ext4.

However, if I can install it with an ext3 format, my Norton Ghost 15 will be able to back up both Windows and Ubuntu.

(1) Is it all right to run Ubuntu 16.04.02 in an ext3 partition?

(2) Can I back up my present installation, reformat the partition to ext3, then restore the backup?

---

### Post by SeijiSensei on 2017-03-22
Yes, you can.  A lot of the differences have to do with maximum file sizes and the like.  For details, see [http://askubuntu.com/questions/44908/what-is-the-difference-between-ext3-ext4-from-a-generic-users-prespective](http://askubuntu.com/questions/44908/what-is-the-difference-between-ext3-ext4-from-a-generic-users-prespective)

My virtual servers at Linode are running ext3 without any difficulties.

---

### Post by steve169 on 2017-03-22
Dear SejiSensei,

Thanks. I now need an answer to a other questions:

[B]1.  Can I back up my present installation using dd, reformat the partition to ext3, then restore the backup?

2.  Is there a better way?
[/B]

---

### Post by oldfred on 2017-03-23
I would stay with ext4 and find a better backup solution.
While reduce performance of Linux just to use one tool.
Ext4 has continued development since releases. Not sure if any fixes to ext3 other than outright bugs.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by sudodus on 2017-03-23
ext3 is not a good alternative.

Use [Clonezilla](http://clonezilla.org) instead of Norton Ghost. It can clone and create compressed image files of partitions with ext4 as well as of NTFS and FAT file systems.

But *oldfred* is linking to many other alternatives for backup. So look closely at several alternatives before you decide what to use. :-)

---

### Post by vanadium on 2017-03-23
For a home user, I do not recommend spending resources in a system backup. Rather spend all that effort in maintaining good backups of your personal data.

- Personal data are unique. When lost, it is lost forever. Your data may also have great emotional value, e.g. pictures.
- Operating systems come for free, in many flavours, and install in less than an hour, slightly more time than the time needed to restore an image. Moreover, the image of your system is quickly outdated.

You have a nice dual boot setup, with a dedicated partition for data storage. Make sure all your personal data are on that partition. Then have a good routine for backing up that data regularly to an external drive. 

Such data backups can be incremental. First time, it takes a lot of time because all data need to be copied. Next time, it takes only a minute because only the changed files are backed up (the more you have worked for the day, the longer it will take :lolflag:).

In Linux, you can conveniently access data from within your home directory irrespective of where it is stored. For this, you replace your regular "Documents", "Pictures" folders by symbolic links, that link to the real location of the data. For the end user (you), these symbolic links behave exactly as a real folder.

---

### Post by steve169 on 2017-03-23
Thanks to all of you. I'll stick with ext4 and keeping working on a backup routine.

---

### Post by RobGoss on 2017-03-23
If you have resolved your issue you can mark this thread as solved, you can do this by using the **Thread tool **at the top of this post

Thanks so much

---

