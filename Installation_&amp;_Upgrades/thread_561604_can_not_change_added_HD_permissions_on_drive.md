---
title: "can not change added HD permissions on drive"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by joeastro@aol.com on 2007-09-27
Mounted a 400gb drive using gnome thing..drive mounted and works. I can not change permissions to /media/obs top drive directory "." so users have 777 permission on the drive.

sudo chmod -R 777 /media/obs
does not work. does not error or say anything.. but 
ls -l 
still shows rwxr-xr-x....root root /media/obs
can not 
sudo chown joe:joe /media/obs
that does notwork
can not
sudo chgrp admin /media/obs
help to change the new drive so all can use it.

---

### Post by Pumalite on 2007-09-27
have you tried:
sudo chmod 777 /media/obs

---

### Post by joeastro@aol.com on 2007-09-28
yes tried all that unix lingo..

sudo chmod -R 777 /media/obs

also changed mod the /obs mount place before mounting HD.

solution was found.
appears that VFAT needs  umask=000 in the fstab !!

this cured the permission flowdown from the 777 at /obs
mountpoint and when you mount -a, all is happy.. the 
permissions flowdown to rwxrwxrwx root root .

other people have had this same problem adding a second
drive. dont know if there are other solutions.

joeastro

---

