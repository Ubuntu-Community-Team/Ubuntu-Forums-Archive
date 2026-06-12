---
title: "/ on ssd and /home on hdd or better to xfer data"
date: 2017-06-16
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-06-16
Would I be better off putting / on an ssd and using Ubuntu's "Backups" to periodically transfer the data saved on the ssd to the hdd? Or is is better to have / on the ssd and /home on the hdd? 

If I were to save files/folders on the ssd for speed, can I use "Backups" to transfer the data over to the backup drive incrementally to the data already on the /home; and then to the external backup hdd?

I do weekly backups in any event.

---

### Post by oldfred on 2017-06-16
I keep / (root) on SSD including /home so my user settings load quickly. But all my data is on HDD in /mnt/data. I do that as I have multiple installs and want to have same data available in all installs, but probably not all /home user settings.

I do use rsync to incrementally copy data from one drive to another. But a copy of data is not really a backup as true back up has versioned copies, so if you edit a file you can go back to a version before the edit. Copy would just overwrite old with newest version.
I also copy most critical files to DVD, flash drive and other systems, and probably not in the most organized way, but what mostly works for me.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 

      
 [https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)
Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[URL="http://www.kirya.net/articles/backups-using-rdiff-backup/"]http://www.kirya.net/articles/backups-using-rdiff-backup/

[/URL]
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first  

[URL="http://www.kirya.net/articles/backups-using-rdiff-backup/"]
[/URL]

---

