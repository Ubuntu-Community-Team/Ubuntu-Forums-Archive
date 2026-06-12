---
title: "Bug: CIFS VFS no response on shutdown/reboot"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Dilligaf on 2009-03-06
This bug has been present since Hardy at least. When a cifs share is mounted in fstab the system hangs on shutdown due to the fact that the network connections are closed before attempting to unmount the mounted shares. More info here [http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/](http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/)    There are several bug reports on launchpad and I can't understand why it hasn't been fixed, admitted I'm not a programmer and there may be more to it. 


Mike

---

### Post by davecgs on 2009-04-04
I'm guessing the problem is because CIFS is developed and maintained by "You KNOW WHO" and that creates a problem maintaining a stable release since they don't release the source code.  CIFS is NOT open source. 

"The YOU KNOW WHO are the guys that gave us a program with the initials DOS"

---

### Post by wigren on 2009-04-20
I came up with a work around for this bug in Jaunty based on the blog post linked to above me. Please let me know if this is a bad way of doing things. The issue is that GNOME brings down the network before it tries to unmount the CIFS shares.

These must be run with sudo or as root:
```
mv /etc/rc0.d/K01gdm /etc/rc0.d/K02gdm
```
```
mv /etc/rc6.d/K01gdm /etc/rc6.d/K02gdm
```
```
ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K01umountnfs.sh 
```
```
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K01umountnfs.sh
```

---

### Post by ThrobbingBrain66 on 2009-04-20
Your solution is intruiging.  This [link]("https://wiki.edubuntu.org/MountWindowsSharesPermanently#Fixing%20a%20CIFS%20bug%20with%20network%20manager") uses the same method as the blog linked to in the OP.  The only difference being using a priority of 15 vs 14.  I would still get occasional hangs even after applying the workaround.

I'm curious, have you encountered any issues stemming from changing the gdm priority?

---

