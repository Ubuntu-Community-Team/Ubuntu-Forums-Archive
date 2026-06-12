---
title: "switch from 32 bit ubutnu 16.04 to 64 bit ubuntu 16.04"
date: 2017-02-07
forum: Installation &amp; Upgrades
---

### Post by newblank25 on 2017-02-07
how to switch to 64 bit ubuntu from 32 bit ubuntu 16.04? thx for help

---

### Post by QIII on 2017-02-07
Hello!

There is no upgrade path, which means you will have to reinstall.

Do you have a separate /home partition?

---

### Post by oldfred on 2017-02-08
This will be a good test of you backup procedures. 
As you can backup list of installed apps, /home and perhaps any manually reconfigured system settings in /etc.
Then you can easily restore system and know backups work well.

I cheat when I do a new install, as I keep old / (root) and install a new / in 25GB. So I make sure new system is working and working the way I want before removing the old install. But I have all data in separate large /mnt/data and very little in /home. So my / can be smaller.

How full is drive?

df -h

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 
I prefer rsync, but there are many ways to backup.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

