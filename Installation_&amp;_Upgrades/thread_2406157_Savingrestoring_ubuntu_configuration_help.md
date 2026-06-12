---
title: "Saving/restoring ubuntu configuration help"
date: 2018-11-16
forum: Installation &amp; Upgrades
---

### Post by yuri-weinstein on 2018-11-16
[SIZE=2]I want to be able to install a new 18.04 version and restore all user settings from my existing 16.04.  Is this possible scenario?

Also wonder what people suggest to use for system restore in case of disasters. 

Thx[/SIZE]

---

### Post by oldfred on 2018-11-16
If standard desktop all your user settings are in /home. Only if server or you have some server applications like database or web may you have folders in / (root) that  you want to also backup. You may want to backup /etc, if you manually edited any system files. I edit several grub files in /etc/default/grub & /etc/grub.d but since I only edit a few files I manually copy into /home, so my backup of /home includes those files.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery

      [/URL]
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810) 
    
       From theFu, more for server or server apps on your desktop install
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986) 
            Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997) 
    [URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

### Post by Frogs Hair on 2018-11-16
Would this be a clean installation or upgrade ? If it will be a clean installation 16.04 and 18.04 have different default desktop environments so I don't think it's possible for that reason. You can install the Unity desktop on 18.04 and manually apply your current settings after installed. No matter if you upgrade or install a new version backup your files to a removable device if possible. The upgrade process is long and problematic for some users.

---

### Post by yuri-weinstein on 2018-11-17
What if we simplified the case and say use on 16.04 only to be able to restore system settings (and maybe apps) on the same h/w or new in case of disaster.  What would you use ?

---

### Post by oldfred on 2018-11-17
In my case I have a very small /home as all my data is in a separate data partition. 
So I have /home backed up and my data partition backed up, but normally do not have to do anything other than mount it in new install.
I also export a list of all my apps. I only change one or two files in /etc, so copy those into /home so automatically included in my backup of /home. I do not backup any other system files and assume I will just reinstall.

I use rsync which is not really recommended for backup, but good for copying. But I resync to another drive, to multiple flash drives at different times. Not necessarily well organized, but works for me.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[URL="http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders"]http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders
      [/URL]
 [https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync) 
    

TheFu is more organized (seems to have managed lots of servers over time) and recommends rdiff which is somewhat similar to rsync.
       Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by yuri-weinstein on 2018-11-18
thank you, need to digest all this information :)

---

