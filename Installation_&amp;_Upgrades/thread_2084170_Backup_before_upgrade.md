---
title: "Backup before upgrade"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by xxlray on 2012-11-14
I originally wrote in [this thread](http://ubuntuforums.org/showthread.php?p=12354284#post12354284) but was asked to open a new one.

The thread explains how to make a system backup before upgrade.

First one should clean the packages a bit:
```
sudo apt-get autoremove
sudo apt-get autoclean
```
(I furthermore suggest to delete some old kernel files from /boot)

Than comes the archive magic:
```
sudo tar -cv --one-file-system --exclude=/home/* --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* -f /home/system-backup.tar /* && sudo chown `whoami`:`whoami` /home/system-backup.tar
```
(fast/no compression - big backup file)
or
```
sudo tar -cvz --one-file-system --exclude=/home/* --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* -f /home/system-backup.tar.gz /* && sudo chown `whoami`:`whoami` /home/system-backup.tar.gz
```
(medium compression speed - medium file size)
or
```
sudo tar -cvj --one-file-system --exclude=/home/* --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* -f /home/system-backup.tar.bz2 /* && sudo chown `whoami`:`whoami` /home/system-backup.tar.bz2
```
(slow compression - small file)

I am thinking about upgradig my Ubuntu. I remember that I had a lot of issues getting the tv-receiver and my graphic card running.

My questions are whether this method will also backup my working kernel and drivers and how do I recover my system from the archive?

---

### Post by oldfred on 2012-11-16
I do not use tar, it is old school, and many now use other tools.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

---

### Post by NikTh on 2012-11-16
+1 for Clonezilla :)

---

### Post by xxlray on 2012-11-17
Thank you. So the answer is "yes it will back up driver stuff" and "use tar -xvpzf nameof.tar.gz -C /  to recover". Note that I was just asking for a one time backup solution and not for a regular one. In my opinion tar is just fine for this issue. (I already have a regular backup solution for the stuff in my home folder)

---

