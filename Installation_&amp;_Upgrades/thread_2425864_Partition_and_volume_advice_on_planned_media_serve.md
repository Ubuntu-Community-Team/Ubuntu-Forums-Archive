---
title: "Partition and volume advice on planned media server build"
date: 2019-08-31
forum: Installation &amp; Upgrades
---

### Post by mmyers1082 on 2019-08-31
[COLOR=#000000][FONT=Arial]Ok server guru’s.  I’m prepping my first full media/shared storage/home automation server and looking for some advice/best practices.  Build details as planned listed below.  [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Purpose built for three primary users plus guest, each with private storage space, shared storage space and host our media library (movies, TV Shows, music, photos).  I will be adding a web front end for one stop easy access to the most frequently used tools and will include a state-of-health dashboard.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I’m not new to Linux/Ubuntu, but this is my first multi-user purpose built server. Previous experience is limited to a single user laptops and RedHat server updates/upgrades, not initial install or setup. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Given two logical drives (1TB RAID1 OS drive, 24TB RAID5 Storage drive), would it be better to just give the 1TB drive for the install or add some partitioning for /var /home /swap … (I’ve read that a /swap partition is faster than the swap file).  And if partitioning is the way to go, what size volumes?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Users:[/FONT][/COLOR]

[LIST]
[*]Myself (Sudo/Admin)

[*]Myself2 (Standard)

[*]Wife (Standard)

[*]Kid (Standard)

[*]Guest (Restricted)
[/LIST]

[COLOR=#000000][FONT=Arial]Server Setup[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Dell PowerEdge T30 (includes 1TB Hard Drive, will add a second for RAID1)[/FONT][/COLOR]

[LIST]
[*]WD Red 8TB NAS Internal Hard Drive (x4 RAID5)
[/LIST]
[COLOR=#000000][FONT=Arial]OS: Ubuntu 18.04 LTS[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Applications:[/FONT][/COLOR]

[LIST]
[*]Samba

[*]Docker

[*]Docker Compose

[*]Portainer

[*]Organizr, HTPC Manager or Muximux

[*]phpMyAdmin

[*]Watchtower

[*]Home Assistant

[*]Transmission

[*]OpenVPN

[*]IPVanish

[*]SABnzbd

[*]Radarr

[*]Sonarr

[*]Plex

[*]Tautulli / PlexPy

[*]Ombi

[*]NZBHydra

[*]Jackett

[*]MariaDB

[*]Nextcloud

[*]Apache2 or Nginx

[*]MakeMKV

[*]HandBrake

[*]Libdvdcss

[*]VLC
[/LIST]

---

### Post by TheFu on 2019-08-31
Only comment is that RAID5 isn't good for huge disks (anything over 1TB).  Use RAID6 or RAIDz2.

---

### Post by SeijiSensei on 2019-09-01
If you haven't purchased the T30 yet, go do so soon, since Dell is selling it for $299 with a coupon code. Great little machine, especially at that price. (I bought mine for about the same price from a third-party reseller at NewEgg who had a bunch of them to move.)

I added another 1 TB disk, and a pair of 4 TB disks in a RAID 1.  I assigned a small partition on sda (512 MB) to /boot, and another small partition (40 GB) to /.  (Most of that space is wasted; 20 GB would easily have been sufficient.) I then partitioned the second 1 TB disk similarly, and devoted the rest of each disk to a partition that I joined as RAID1 with mdadm.  I mount that device (about 900 GB)  as /home.  I also set aside a small portion of the second 1TB disk for swap.  The other RAID1 array is mounted as /media/raid and contains things like my video archive.

I also have a [USB 4 TB drive]("https://www.newegg.com/seagate-model-stdr4000100-4tb/p/N82E16822178781") that I use for nightly backups. I run a script that sucks down files from three cloud servers at Linode, from the local server, and from another machine connected to my TV.

I haven't increased the memory from the original 4 GB it shipped with.  Less than 1 GB of swap is in use, and about 1.2 GB of physical memory is devoted (dynamically) to buffers and disk caching.  This machine runs a mail server, a PostgreSQL server, Samba, an NFS server, minidlna, ntpd, apcupsd, and the KDE desktop.  (I'm using CentOS 6.)  I'd probably have a lot more free memory if I got rid of the GUI.

Since you have some RedHat experience, one thing you may notice right away is that home directories in Ubuntu have 755 privileges rather than the 700 privileges RH uses.  This can be a privacy concern (like do you want your kids being able to view your files).  I wrote about this issue and how to create a shared data area in this post: [https://ubuntuforums.org/showthread.php?t=2424509&p=13878755&viewfull=1#post13878755](https://ubuntuforums.org/showthread.php?t=2424509&p=13878755&viewfull=1#post13878755).

---

### Post by mmyers1082 on 2019-09-01
I appreciate both your responses.  
@TheFu, thanks for the RAID suggestion, great catch.  
@SeijiSensei, it's sounds like I made a good choice with the T30.  I was aware of the privileges and already planned on dedicating the time to set some privacy to the accounts (well, the kiddo will be monitored, but the wife will have her private space as will I).  I will be reading your linked post though.  I may mirror what you've done except that due to the size of my media library (~10.5TB and growing), RAID 1 for the media space would just be too expensive.  Great insight though!

---

### Post by TheFu on 2019-09-01
I don't use RAID for media.  A good delayed mirror is used.

For the OS, apps, personal files and settings,  I use a real backup tool that does versioning efficiently. Versioning of media files is storage prohibitive, so those files aren't ever kept in a HOME directory.

I use RAID1 where HA is required, like for VM guests.  That has nothing to do with my media/nfs/calibre server.

For me, storage architecture is all about backups and DR plans.

---

