---
title: "Apache2 under Xubuntu - cant set document root to mounted HD."
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by apresvoop on 2008-04-13
I'm having trouble getting apache to recognize a new document / home directory for the site which is on a mounted hard drive.  The main HD that apache is installed on is fairly small, and will not be big enough to hold the website (a gallery).

The drive is named "New Room", and thus the path for the directory is going to be /media/New Room/HTTP.  Now apache will not recognize this, and I can't figure out the device name (it's not sba1 or sba2).  Nothing does show up under /mnt.   I have to access the drive, type in my root password, and then it'll show up under /media.

I've tried setting Directory "/media/Extra Space/HTTP"  but that still doesn't work.

Any thoughts on how I can get this working?  

Or maybe to simplify things, how do I rename a drive?  I've done google searches, but all I come up with are results for installing Ubuntu from a USB drive.


Thanks.

---

### Post by mohammadrizki on 2008-04-14
Hi there,
What do you get when you do:
> df -h
If it is mounted correctly, you should get your hard drive listed there.  And starting from there perhaps we can manage how to get things work.

---

### Post by apresvoop on 2008-04-29
Sorry for not getting back to you sooner.  I got way to caught up with the outside world and forgot I even posted this thread.   But when I do "df -h" in the console, I get:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.0G  2.9G  5.7G  34% /
varrun                125M  116K  124M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   48K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   38M   87M  31% /lib/modules/2.6.24-16-generic/volatile



But this is after I upgarded to 8.04.   Right now it's not even appearing anymore.  I can see the drive in BIOS, but not quite sure how to go about mounting it from here.

Anyway advice on how to proceed is appreciated. :)

---

