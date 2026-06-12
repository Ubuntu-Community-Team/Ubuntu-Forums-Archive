---
title: "Segmentation fault in restarting ubuntu"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by yanyan on 2008-02-28
When trying to restart Ubuntu machine after not using it for some time, it showed me error message on the screen as:

/etc/rcS.d/S85urandom:line 39: /bin/rm: cannot execute binary file
/etc/init.d/ rc: line 160: 4289 Segmentation fault  grep -w -q quiet /proc/cmdline 2> /dev/null
/etc/init.d/rc: line 166: 4290 Segmentation fault stty onlcr < /dev/ console > /dev/console 2 > &1
and something like following:
chown: changing ownership of '/var/log/mail.warn': Read-only file system. and sos on.
.....


I really could not understand why such kind of error message could show up. My machine used to run on ubuntu 7.04, later, I upgraded it and for almost one month, it does not have any problem. 

I have another machine, I also upgraded it from Ubuntu 7.04 to 7.10 and later it showed same error message. At that time, I thought it could come from virius. So I formatted the disc and reinstalled the ubuntu 7.10 from CD. But this machine has a lot of useful data. How to save it? thanks a lot.

---

### Post by Pumalite on 2008-02-28
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

---

