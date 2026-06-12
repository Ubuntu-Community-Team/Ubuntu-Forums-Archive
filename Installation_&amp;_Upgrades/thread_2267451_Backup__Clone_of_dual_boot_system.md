---
title: "Backup / Clone of dual boot system"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2015-03-01
Finally have what appears to be a stable dual-boot Ubuntu 14.04 / Windows 8.1 system and now want to move on to backup.  I've read many posts about backup strategy, most of which suggest that cloning may be an un-necessary overkill (and a Windows-centric concept).  Nonethless, I want to make one clone of a clean dual-boot install before I start using it in earnest.  

I've read that using dd will work but can take a long time.  Question is how long is long?  Mine has been running 18 hours now for a 750GB drive (attached via USB 3.0) but I can't tell if something is hung or how far along it is.  How do I know when to give up and try something different?

---

### Post by oldfred on 2015-03-02
Using dd is probably the most difficult/slowest way. It has to also copy all blank space. It is intended for exact size to exact size copy. Speed depends totally on system. 
And with gpt you cannot copy just partitions but only entire drive as internal GUID as well as UUIDs must match. You may be able to use sgdisk and fix up a copy but not for normal backup.
       from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

Most use Clonezilla for image backups.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

But I find I can easily reinstall and restore in less than an hour. So I use rsync to backup my /home, data and some configuration files. And export a list of installed applications. Then I can fully restore system or update to a newer version and reconfigure it.

I originally started with this, and then added & updated details for my own configuration.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

But now I am evaluating converting to this:
 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by ken18 on 2015-03-02
Clone using dd finally finished after 28+ hours, and that's for a 750GB hdd.  Think of what it would be like for a 4TB drive!  I agree about being able to re-install Ubuntu in a relatively short period of time, but Windows is a different story.  It probably takes a day to re-install Windows 8 from recovery partition / media, perform all of the updates, then upgrade to 8.1, then perform a lot more updates, then install apps, etc.  I think I really need a good imaging and/or cloning method.  Thanks for the info.  I'll likely try Clonezilla next.

---

### Post by oldfred on 2015-03-02
Others have suggested these for Windows. I have not used Windows since XP so do not know.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by ken18 on 2015-03-02
Thanks for the tips.  I've already tried Macrium Reflect with mixed results (images seem to work, but my last clone failed to boot Windows).  Never heard of DriveImage XML but will look into it.  I suppose I could use different tools for the Windows partitions vs Linux partitions.  Actually, Windows 7/8 has a built-in system image utility that seems to work well, but (not surprisingly) it ignores any non-windows partitions (took me quite a while to figure out that it wasn't updating the Linux partition until I actually formatted it beforehand).  For now I think I'll use a single tool for all partitions, which points me in the direction of Clonezilla.  I'm now quite skeptical in general of any Windows based tool.

---

