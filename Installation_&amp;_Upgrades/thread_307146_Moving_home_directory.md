---
title: "Moving /home directory"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by dr.lnx on 2006-11-26
hi, i have a partition, /srv, that contains /srv/home /srv/www /srv/public and /srv/mysql now i want to say the system that /home is in /srv/home. how could i do that in the best way?
for the moment i made a link but i think there is a better way!

tanks by

---

### Post by hal10000 on 2006-11-26
It's really unusually for a desktop-system to change /home to this directory, because the content of /srv is usually thougt to be a mountpoint (or directory) for server-programs like apache or mysql-databse to put their stuff there.
But if you are really sure you want to do that, then you might do the following:

1. copy the content of /home to /srv/home: [COLOR="Red"]sudo cp -a /home/* /srv/home[/COLOR].

2. Backup (as root) the file [COLOR="Red"]/etc/passwd[/COLOR]. Edit (as root) [COLOR="Red"]/etc/passwd[/COLOR] and change the homedirectories of every user from [COLOR="Red"]/home/username[/COLOR] to [COLOR="Red"]/srv/home/username[/COLOR]. Do this _only _for users whose homedirectories reside in /home/username. The homedirectory in the /etc/passwd file is the second-last field (fields are separated by a colon.

3. For every new user you create, you have to point his homedirectory to /srv/home/newuser.

4. logout and login again; your new settings should take effect.

5. If everything works fine, you can delete the contents of the old /home. But I would recommend not to delete /home itself. (Wait a few days/weeks before you delete the contents).

---

### Post by taurus on 2006-11-26
Or just change the mount point from /home to /srv/home in /etc/fstab if you have a separate partition for /home!!!

---

### Post by dr.lnx on 2006-11-26
also, my system is a server and all the home are shared trought nfs and samba .
in fstab can i write
/home         /srv/home    defaults ......
???

---

