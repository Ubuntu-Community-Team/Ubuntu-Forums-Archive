---
title: "Mouse and Keyboard not working on changing to Gnome classic"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by nipunreddevil on 2011-10-25
I had recently upgraded from 11.04 to 11.10
I made my machine auto logon
I changed the default session to gnome-session
Now when Ubuntu starts i see only a "X" instead of a cursor.Mouse and keyboard don't work
I can however start from root using the recovery mode.
How can i ensure that i have a clean start.I also have kubuntu-session and xfce installed

---

### Post by nipunreddevil on 2011-10-25
I also installed Linux INternals on Windows and i can edit any file on my Ubuntu partition.
Would changing some configuration file help me login normally or maybe disable auto login.

---

### Post by nipunreddevil on 2011-10-25
```
Create or modify the file /etc/gdm/custom.conf, and write the following content:

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=enzotib
AutomaticLogin=enzotib
TimedLoginDelay=30
DefaultSession=gnome
where enzotib should be replaced with your username and gnome could be replaced by

gnome - for Ubuntu
gnome-classic - for Ubuntu classic
gnome-2d - for Ubuntu classic (no effects)
```
This seems to be the solution.
But how can i edit this file from recovery mode?

---

### Post by nipunreddevil on 2011-10-25
I tried editing /etc/gdm/custom.conf using nano and vi
But it opens as a read only file.
How can i change it's contents as per my previous comments

---

### Post by nipunreddevil on 2011-10-25
I tried using Edubuntu Live CD.Using it i was able to mount NTFS drives but not my Linux parition.I guess i was using an older version of Edubuntu(7.10) which might not support newer Linux filesystems
I also tried DSL Live USB,which didn't look impressive.Wasn't able to do much from it.
Currently downloading CentOS live.Is there some other small yet useful LiveCD which shall let me mount my Linux partition and change this conf file

---

