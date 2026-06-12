---
title: "Trouble setting up RAID 1"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by brad58 on 2016-06-21
I have a server with 7 drives.  two are 4TB, two are 2TB, and three are 1TB.  I am attempting to install a new Ubuntu installation.  I want to use one of the 1TB drives as my boot drive (I plan to replace it with a SSD to improve performance, just testing with it right now).  I then want to create a 7TB RAID1 system with the remaining drives.  I'd even settle with just a 4TB RAID1 system with the two 4TB drives.

When installing Ubuntu I did the manual partition configuration.  I created a RAID1 set-up with 2 active drives and 0 spares.  I selected my two 4TB drives as the active drives.  I then created a LVM using one of the 1TB drives.  I set the 1TB as bootable and the /root drive.

When booting into the system, I can't see the RAID drives.  It seems like I only have 1TB.

```
bphillips@HTPC:~$ df -hFilesystem             Size  Used Avail Use% Mounted on
/dev/mapper/BOOT-BOOT  909G  1.3G  862G   1% /
udev                   3.9G  4.0K  3.9G   1% /dev
tmpfs                  1.6G  428K  1.6G   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   3.9G     0  3.9G   0% /run/shm
```

Are my RAID drives there? If so, how do I see them and access them?

My intended use for the server is to make a HTPC using Kodi.

---

### Post by mastablasta on 2016-06-21
> **brad58 said:**
> 
My intended use for the server is to make a HTPC using Kodi.

an overly complex setup for that. i am not sure why LVM is necessary here... why do you even need RAID? RAID is guarding against disk failure (it is not a backup solution). videos and such are static data you can back them up once (if you need to) for example to external disk and and that's it. with kodi you then just need to setup autobacup of database and you are done.

SSD is awesome to have, but again i am not sure what kind of load this machine will have. i use the old ModelB raspberrypi with external drive attached to it. it has an SD card. sure it may take some time to reboot (which is one or two times per year) and it can't run some of the fancy skins and effects but otherwise it (using Amber skin) performs well. i am not sure why i would use an SSD. ifpossible i would get it a real hard disk for the OS but even that doens't seem necessary. i can browse easilly, the interface is fluent and responsive. and all that on 8Gb cheasp SD card which sitll has plenty of space left for the OS.

data on external disk occasionally takes osme time to access (a couple of secs) as the disk powers down a lot when not in use. so it needs to sping up and get the file form it. still once it spinns up again it is all fast and responsive.

---

### Post by brad58 on 2016-06-21
Thanks for the reply.  I suppose I am overthinking this by using a RAID.

---

### Post by mastablasta on 2016-06-22
in my opinion, yes. RAID would be useful on soem server where data is constantly or regularly changing (e.g. backup server with regular often backups, website server...). that way if one disk fails you can replace it and continue with the work knwoing you have the latest data available at all times. video pics are static files. disks usually are not constantly spinning or in use and data is usualyl recorded sporadically and then not altered.

one more thing re RAID - corrupted data on one disk transfers to the other. :)

---

