---
title: "Transferring data to new HD"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by Maskedrose on 2012-08-27
Hello All! I've been using Ubuntu since last year so while I'm not a complete newb, there are still a lot of things that I am learning about the system that feel very overwhelming... TAR, dd, etc. Anyway, I've got a bad sector and my HD is rather old and slow anyway (I built a new system but didn't have a new HD on hand so I used what I had lying around)

I'm on the fence about buying a SSD or another HD.. SSD is still a bit expensive for the price but I bet I can get a good deal from Amazon towards Christmas. 

Anyway, I was wondering about the most effective method to completely transfer my OS to the new drive... My understanding is if I get an SSD, I could corrupt the system by copying everything over using a backup since certain files were written for the HD and are deleted/new system on an SSD would not know how to read the files blahblah etc. I'm also running Gnome desktop if that is relevant to this discussion... 

I've been browsing the forums for a few weeks to read up on this, but I don't feel very confident yet about the procedure. Do I need to have both discs connected and run a pipe from HD to SSD(or new HD) or could I back up directories to a disc/usb and then copy them to the new drive? etc...

If this has been discussed, or there are some commands involved(why type all of that?) feel free to link me to that thread!

Thanks!!

---

### Post by oldfred on 2012-08-27
Lots of issues. 

I recently added a new 60GB SSD. I still consider it a luxury, but system boots really fast and loads larger programs instantly. But I cannot type any faster nor are Internet downloads any quicker. :)

I prefer clean installs. dd and related copy programs are for same size to same size copy & copy even the blank or empty bits also. Many suggest clonezilla.

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)
But do not use dd for copies from MBR to gpt partitioned drives
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

But you should be backing up your data anyway.
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I believe in clean installs and restore from backups. If only using Ubuntu you do not need a large SSD, but then need another rotating drive for data. I have 2 / (root) on my 60GB drive and aggressively move data from /home into /data on my rotating drive.

Uses alternative or text based installer on installing to SSD:
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

Lots of detailed info:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

