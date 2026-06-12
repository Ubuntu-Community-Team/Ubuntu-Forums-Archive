---
title: "Need help with AFP (Netatalk) and missing drives"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by thorlin on 2008-04-23
I've spent the better part of the last 2 weeks trying to figure out the best way to build a home file server for my home network which consists of a MacBookPro and an iMac.  I've settled on a Ubuntu server.  I'm running 7.10 and have it configured with Netatalk using SSL for encryption of passwords.  However, I can only see one drive when I attempt to connect to the server.  Here is a quick description of my setup.

Dell PC
Ubuntu Server 7.10 running LAMP and OpenSSH
2 physical HDD
Drive 1 (SDA) is an 80 GB with 3 partitions.  
Partition 1 - 38 GB system partition mounted at /
Partition 2 - 1.7 GB swap partition
Partition 3 - 40 GB logical partiion mounted at /home
Drive 2 (SDB) is a 500 GB drive with 2 partitions
Partition 1 - 200 GB logical partition mounted at /media/files
Partition 2 - 300 GB logical partition mounted at /media/storage

Through SSH I can browse to these drives no problem.  And when I browse to the server "vlhomeserver" through the Finder in OS X (Leopard) it will connect no problem, but it only displays the /home drive.  If I try to go to any other drives /, or /media/files, /media/storage Finder tells me the volume media/files cannot be mounted.  I'm not sure if I'm missing a configuration on Ubuntu.  

I'm not a techno-idiot but I'm just beginning to grasp Linux.  Anyone have any suggestions?

---

