---
title: "Another Dual Boot Post: Removing Windows 10"
date: 2019-01-21
forum: Installation &amp; Upgrades
---

### Post by bradleywyros on 2019-01-21
Hi everyone,
I know there are many posts about this, but as we know, each dual boot is (somewhat) unique. I currently have Windows 10 dual-booted with Ubuntu 18.04 on my Asus Zenbook. I don't have a need for Windows on the machine any more, so I'd like to remove it. I'm just not exactly sure what to delete and what to resize. I've read some posts and I'm assuming I need to delete 2 and 3, but as you can see, I have two Linux partitions, home and root. I created these because I was just doing what I was told when following a tutorial for dual booting, so I'm not quite sure how they need to be resized after the Windows deletion. I'll also need to set my GRUB to auto boot Ubuntu. If anyone could step me through the process, that would be great! 

PS, this screen shot is from the Live USB I created for the original Ubuntu dual boot installation. Thanks again!

 [ATTACH=CONFIG]282265[/ATTACH]

---

### Post by oldfred on 2019-01-21
Fully back up Windows.
Many users come back with one app or game they just have to have that does not work in Ubuntu and need Windows back again. Or later want to sell system and it needs Windows to sell it.

You can remove sda2, 3 & 4. I might then make the space you had for Windows as /home as your /home is small.
You can remove /EFI/Microsoft folder in the ESP - efi system partition and Windows boot entries in UEFI.

While not moving /home from a folder inside /, but from one partition to another you can use this.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 
    
You may be able to just use gparted to copy partition. 
But difficult to expand as you have to move / left then expand right. Then move /home left and expand right. Moving left has higher risk as it must copy all data which can be slow. Be sure to have good backups.
If partition copied or new created, you will have to change the UUID in your fstab. 

Once sure copy of /home is completed & working you can delete old /home and expand / right into space from the old /home. The 40GB is only slightly more than what I normally suggest (25 or 30) for /.

---

### Post by bradleywyros on 2019-01-22
Would it be ok/advised to keep my /home and /root and just resize them properly after windows is deleted? and then just update my grub with sudo update-grub? I think I'm a little confused by what you are saying I should do with /home.

---

### Post by oldfred on 2019-01-22
I was saying resizing is difficult (but not impossible). I do not like to move partitions left which you would have to do. It is slow as it has to copy everything. You only can expand right, after the move left & that would normally be quick as no data to copy.
The expand left can take a long time, and any interruption at all, by user or power failure, totally corrupts install as part of data is in one place and part in another. Or you must have really good backups.

Another alternative is just to do a new install with 25 to 30GB for / and rest for /home. Then restore your backup data. 
You could temporarily keep current / & /home as not large. Once data restored from backups, then you delete old / & /home and expand /home into new empty space. That could be test of your backup procedures as temporarily you will have old install to boot into, if you forgot to backup something.

You first should have good backups whatever you decide to do.
Some like image backups, others prefer each file be backed up. 
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools) 

      
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[URL="https://ubuntuforums.org/showthread.php?t=2377810"]https://ubuntuforums.org/showthread.php?t=2377810

      [/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 
    [URL="https://ubuntuforums.org/showthread.php?t=2377810"]
[/URL]

---

