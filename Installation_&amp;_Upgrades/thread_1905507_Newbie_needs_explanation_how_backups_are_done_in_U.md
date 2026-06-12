---
title: "Newbie needs explanation how backups are done in Ubuntu (Kubuntu)"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by clicklisa on 2012-01-07
I'm using Kubuntu 11.10 64-bit. I have 2 partitions (root + home).

How do I make a backup so that I can restore my system to the exact state it was in? I know I could use Clonezilla to make an image. But 'home' is on the second partition which is more than 200GB. I don't want to save everything from my home folder. For example, I have 100GB of files in download. But these are unimportant and I don't want them to backup.

I just want to make a backup of the system and how I configured it, including the software I installed (and how I configured that software).

On top of that, I don't have an external hard disk. Do I need to re-partition my hdd and reserve extra space for the system backup? What things exactly do I have to backup to get back the settings of the system, with all the installed software, plus the settings of that software, but without saving all the other files from 'Pictures', 'Video', etc?

And how do I restore from such backup?

---

### Post by mastablasta on 2012-01-07
you do need separate partition (if you don't have external drive). you must be careful later nto to format it or delete it during reinstall.

simplest way would be to use Linuxmintbackup tool: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

you can then back up the settings and when you back up your /home you can select what you want to back up and what not. you back it all up into different parition (you created before) or external disk. note here that if it's just data (e.g. pictures) you can just copy it, you do not need special tool for it. 

for more backup options including bare metal bit by bit backup see my signature...

---

### Post by clicklisa on 2012-01-07
That MintBackupTool looks promising. Does this work with Kubuntu 11.10?

---

### Post by raja.genupula on 2012-01-07
> **clicklisa said:**
> That MintBackupTool looks promising. Does this work with Kubuntu 11.10?

yes you can man 
go with this

[http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

All the best.

---

### Post by oldfred on 2012-01-07
One of the advantages of Linux is that there are a lot of alternatives, but sometimes that can be confusing as there are so many.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I plan on a new clean install so I do not do the full image backup. But hard drives fail so I backup to another hard drive regularly. But the backup could copy a defective file or have other issues, so I burn a DVD of the most important data on a regular basis. Configuration, photos, some programs I am makeing, financial info etc are what I consider most important. Music I can rerip if I have to so I do not back it up and some other things I may only partially back up. It depends on what you think is important. But you have to assume worst case of a total hard drive failure. 

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by clicklisa on 2012-01-08
> **raja.genupula said:**
> yes you can man 
go with this

[http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

All the best.
I'm not a man :)

Unfortunately, that ppa is not available for Oneiric :-/

> 
W: Failed to fetch [http://ppa.launchpad.net/webupd8team/mintbackup/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/webupd8team/mintbackup/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/mintbackup/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/webupd8team/mintbackup/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/mintbackup/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/webupd8team/mintbackup/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mastablasta on 2012-01-09
but it should still work.
 
you could try with a .deb file:
[http://packages.linuxmint.com/pool/main/m/mintbackup/](http://packages.linuxmint.com/pool/main/m/mintbackup/)

---

### Post by oldrocker99 on 2012-01-09
I have 2 1TB drives; dual-booting Windows 7 and Mint 12 on the first, and my huge /home folder on the other. I use FreeFileSync to coordinate my /home folder with an external drive, and it works very well. RealTimeSync will back up everything you write (or delete) between two folders, too.

---

