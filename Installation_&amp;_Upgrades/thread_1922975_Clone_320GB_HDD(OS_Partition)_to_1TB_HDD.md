---
title: "Clone 320GB HDD(OS Partition) to 1TB HDD"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by apt-get install help on 2012-02-09
Hi 

I am considering buying or building a new system. My new rig will have a 1TB HDD which will have the OS partition and all my data on the same drive, but I would like to make a clone of my current 320GB drive using Redo Backup software and then copy the clone backup on to my new systems drive.

Will I be able to archive this with out data loss, or will I have big problems with the Ubuntu partition that is on the old drive and just copying it on to the new one.

Thanks :)

---

### Post by winh8r on 2012-02-09
You can do exactly what you need using CloneZilla


more info or get it at:


[http://clonezilla.org/]("http://clonezilla.org/")


hope this helps

---

### Post by deonis on 2012-02-09
+1 to the previous post

---

### Post by oldfred on 2012-02-09
You can do that, but it makes a difference if you want to keep 320GB drive on new system? If not it is easier as you will not have the issue of duplicate UUIDs. If a new system, some settings may not be  correct, but that usually is video or wireless Internet related and can be updated. You will probably have to reinstall grub2's boot loader.

I tend to prefer clean installs as that then does a houseclean of all the old cruft, log files etc. You can connect drive or network it,  and copy /home and possibly some other data from old drive to new drive.

---

### Post by apt-get install help on 2012-02-10
> **oldfred said:**
> You can do that, but it makes a difference if you want to keep 320GB drive on new system? If not it is easier as you will not have the issue of duplicate UUIDs. If a new system, some settings may not be  correct, but that usually is video or wireless Internet related and can be updated. You will probably have to reinstall grub2's boot loader.

I tend to prefer clean installs as that then does a houseclean of all the old cruft, log files etc. You can connect drive or network it,  and copy /home and possibly some other data from old drive to new drive.

 I was thinking about it and I relised that my current system is 32 bit and the new one would be 64 bit, so cloning the drive might have issues as my new system would have 8 or 16GB RAM so I would have problems with the swap space on the drive.  Also could I just copy my home directory using clonezilla or Redo Back Up software?

---

### Post by brpylko on 2012-02-10
Running
```
sudo dd if=/dev/sda of=/dev/sdb
```should work (assuming you are cloning sda to sdb).
It will take a while and there is no progress indicator so I would leave this overnight.

---

### Post by oldfred on 2012-02-10
If you can plug drive in even temporarily, you could just rsync it. Or if you have a network use it to rsync the /home over.

Copying it would be something like moving /home.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh


Also you want to make a list of installed applications.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade


Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Files to include or exclude from full system backup.
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)


[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by apt-get install help on 2012-02-11
> **brpylko said:**
> Running
```
sudo dd if=/dev/sda of=/dev/sdb
```should work (assuming you are cloning sda to sdb).
It will take a while and there is no progress indicator so I would leave this overnight.

 Thanks for the help  I have a question about whats been posted, can I use an NTFS external drive for all the system backup solutions that have been suggested. I have data already on the drive.

---

### Post by oldfred on 2012-02-11
NTFS does not support permission nor ownership, so you cannot copy files over without issues. But if in a compressed state like with tar or some of the others it should work.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

---

### Post by jmate24 on 2012-02-11
I would suggest a clean install then copy the data from your old 320GB /home partition to the new one but remember only copy what's in the visible folders and in your .ubuntuone/Purchased From Ubuntu One folder so that you may keep your music that is purchased but as for your games that you purchased I suggest that you keep the 32-bit system and just play your games that you purchased on it. And use the 64-bit system for school/work or for your music and videos. (An NFS or sharing them over Samba would be cool too.)

---

### Post by apt-get install help on 2012-02-13
I will give all the above solution a closer look when I get my new system.

---

