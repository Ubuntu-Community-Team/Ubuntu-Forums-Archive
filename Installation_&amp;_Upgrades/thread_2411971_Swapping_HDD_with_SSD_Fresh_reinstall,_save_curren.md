---
title: "Swapping HDD with SSD Fresh reinstall, save current settings?"
date: 2019-02-06
forum: Installation &amp; Upgrades
---

### Post by smittylube on 2019-02-06
I have e Dell E5500 with dreadfully slow 2g processor and 2g ram and an old hdd.

I have 4g ram and a new SSD to install. 

I loaded ubuntu a few days back got a pretty good feel for it. Found a couple of programs I use and all works well. Loaded up a theme and such.

I don’t have any real files that I need to save, but would like it to be where I am now just minus the dual boot with win7.

I burned a dvd with the 18.4. ISO to install so I’ll reuse this.

Should I save/ copy/ backup my entire .home file system to a thumb drive, swap drive and then restore from backup?

thanks for the help and all the fun.

Steve

---

### Post by oldfred on 2019-02-06
Your /home is all your data, unless you also have separate data partitions. Is your /home inside / (root) or a separate partition?
You can also export a list of installed apps, to make it easy to reinstall.
Only if you made some system setting changes, may you also want /etc. But if new install is different version or different system, you may not want to just restore as settings may be different. 

This is a good time to test your backup procedures as you still have old install to go back and get anything you missed.
       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
      [/URL]
 Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810) 
            Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) 
    
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 
    

[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

