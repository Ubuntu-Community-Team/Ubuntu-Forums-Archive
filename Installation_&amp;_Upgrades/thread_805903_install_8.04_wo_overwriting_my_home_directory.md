---
title: "install 8.04 w/o overwriting my /home directory"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Darth_tater on 2008-05-24
is it possible to install 8.04 without overwriting my home directory...

i understand how his would be possible if they were on multiple partitions, but this is all one single partition.

i ask, because inside of the home directory, there are hundreds of folders, each with a unique permission set, and i don't have an easy way t back them all up *and* keep the security permissions in effect.

any help you could provide would be wonderful.

---

### Post by Pumalite on 2008-05-24
Only if you have /home in a separate partition. Otherwise, save data and do a clean install.

---

### Post by Darth_tater on 2008-05-24
that's what i was afraid of.

can anybody give me a script, that i can run inside /home and it will record every file, folder and its permissions?  that way, i can reformat, making a new /home partition but still keep my folders and their permissions.

i cant imagine it would be difficult for a linux CLI guru

---

### Post by Pumalite on 2008-05-24
You might want to try this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Darth_tater on 2008-05-24
oh, i know how to do it... in fact most of the guide is useless because (IIRC) 8.04 installer will do this for you.

my problem is that i need to backup my existing /home folder and all its unique files and folder permissions onto something else, reformat and make a new home partition, and then recopy the information back over.

if i just take an old removable hard drive and format it to ext3 can i copy my entire home directory there and have my file/folder permissions remain intact ?

---

### Post by Pumalite on 2008-05-24
Take your pick:
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by eldragon on 2008-05-24
boot the live cd,
run gparted
resize your existing / partition with the home dir to your liking (make sure to leave it to the end of the drive, next to the swap partition).
create the new / partition on the left free space at the beginning of the drive
mount the old partition. and move all homes to the / of that partition, (first delete all folders / files except for the home folder).
run the installer, but remember to pick your / and home partitions accordingly.


hope im clear enough.

---

### Post by IgnorantGuru on 2008-05-24
If you're just looking to copy your /home folder with permissions, I would suggest using the cp -a option (archive, which copies the files without changing permissions or ownership).

```
sudo cp -a /home /other/home-backup
```

where 'other' could be on a removable drive, USB stick, etc.

Then to restore it, before logging into gnome or KDE, press Ctrl-ALt-F1 for a console, login and enter:
```
sudo mv /home /home-orig
sudo cp -a /other/home-backup /home
```

Just make sure that when you set up your new install, the users have the same UID and GID as the old system.  cp -a stores the UID/GID of the file, not the username.  So if user1 was user 1001 on the old system, make sure it is that on the new system.  (Easiest way is to add the users in correct order.)

You could also tar and untar it with permissions intact.  When extracting use the -p option (default for root anyway).

Also, when you setup your new system, consider making some additional partitions.  My suggestions are here...  [http://ubuntuforums.org/showthread.php?p=2148017#post2148017](http://ubuntuforums.org/showthread.php?p=2148017#post2148017)

---

### Post by Darth_tater on 2008-05-24
> **IgnorantGuru said:**
> If you're just looking to copy your /home folder with permissions, I would suggest using the cp -a option (archive, which copies the files without changing permissions or ownership).

```
sudo cp -a /home /other/home-backup
```

where 'other' could be on a removable drive, USB stick, etc.

Then to restore it, before logging into gnome or KDE, press Ctrl-ALt-F1 for a console, login and enter:
```
sudo mv /home /home-orig
sudo cp -a /other/home-backup /home
```

Just make sure that when you set up your new install, the users have the same UID and GID as the old system.  cp -a stores the UID/GID of the file, not the username.  So if user1 was user 1001 on the old system, make sure it is that on the new system.  (Easiest way is to add the users in correct order.)

You could also tar and untar it with permissions intact.  When extracting use the -p option (default for root anyway).

Also, when you setup your new system, consider making some additional partitions.  My suggestions are here...  [http://ubuntuforums.org/showthread.php?p=2148017#post2148017](http://ubuntuforums.org/showthread.php?p=2148017#post2148017)



this is *exactly* what i needed

right now, i an shrinking the main system partition, then i will copy everything over to a new partition

then ill delete the ole one and re expand the new one so that it takes 95% of the disk and the system partition gets the other 4.5% and swap gets .5%

thanks a ton, everybody... i think i have what i need to get this done.

---

