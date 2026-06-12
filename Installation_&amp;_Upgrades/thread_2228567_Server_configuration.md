---
title: "Server configuration"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by error2 on 2014-06-08
Hello,

I want to install Ubuntu Server on my HP Micrsoserver. I have 1 SSD and 2 HDDs.

The SDD should conain only the system and it's necessary ressources, while the HDDs should be in (software)RAID 1 and contain all my data.

The server will be used for network storage (movies, documents, music,...) and for some services, like sql-databases and websites.

And alle the stuff mentioned in the sentence above(data, websites, databaes, programm repos,...) should be on the HDDs.

My problem is, that I am not quite sure how I should configure the partitions, like which folders(/home,/var,...) should be on the HDDs, which on the SSD and how much GB they shoould get.


Note:
SSD -> Samsung Evo 120 GB
HDDs -> 2x1TB Western Digital Red (software RAID 1)

---

### Post by TheFu on 2014-06-08
Excellent questions!  

First, do a base install with just ssh - nothing else.  Setup remote access from another system. Do not touch the HDDs yet.
I wouldn't put your HOME on the HDDs either. If there is an issue with the RAID, your settings may not be available.  Good backups of the system and HOME to the RAID drives will be helpful should/when the SSD fails.

Then I'd make a top directory, like /d/ to mount the RAID onto.  If you want, create a softlink from ~/d/ to /d so that easy access to the data area is possible.

I'd make /d/backups/ to hold backups from any systems on the network, including itself.
/d/M/ for movies
/d/Music/ for ... 
/d/www/ for ... ... and just create a link from /var/www to /d/www/ so that apache/nginx default configs "just work."

Be cautious with directory permissions, especially if this system is available to the outside world (on the internet).  Being hacked means all files on the system can be accessed by anyone in the world.

I'd only allow sftp connections for file transfers, unless the system is not serving the internet. If  that is the case, NFS and Samba are fine for local access only.

Secure ssh, scp, sftp with **fail2ban**.

I'd highly recommend using Plex as the media server, but know that transcoding for specific devices on this machine really isn't an option. The CPU isn't powerful enough.  It should be fine for simple websites, small webapps and serving files, however.

Definitely put on your security hat if you want to make anything available to the internet.

---

