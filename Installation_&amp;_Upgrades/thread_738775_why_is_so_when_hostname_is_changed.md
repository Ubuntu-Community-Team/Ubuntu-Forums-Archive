---
title: "why is so when hostname is changed??"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by acidsolution on 2008-03-29
Mine Ubuntu Box was working fine . I decided to change hostname so i edited file 
```
/etc/hostname
```
After changing mine hostname  mine application stops working whenever i open any  application like firefox or evolution mail it just starts and than  vanishes but its process continues .
i restarted mine machine to find myself in trouble i cannot restart mine machine it  gave error like gnome setting cannot be loaded or sumthing like that .
Before i realize that this was because of changing hostname i wasted mine 2 hours trying to find out the cause and trying mine best to remember what settings i might have changed  from last reboot.
finally i rebooted on recovery mode and changed mine hostname to old one and restarted .
to my surprise mine ubuntu box started working fine for me again .
Why is so can any one please explain .
how can i change hostname so that mine box works fine ?
:confused:

---

### Post by alan34 on 2008-03-29
Found this

[http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/](http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/)

Think it means although you edited the correct file /etc/hostname you must run the script

sudo /etc/init.d/hostname.sh start         

to set other files with the new hostname. Please be cautious I have not tried this.

Good luck

---

### Post by thotmos on 2008-05-20
worked with me, after a restart. thanks alan34

---

