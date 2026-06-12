---
title: "Alert message after reboot - new install"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by kurtwp on 2010-01-05
At first I tried the using the CDROM to install the server but around 8% through it could not talk to the CDROM anymore.
I did attempt this a few times including re-seat the CDROM and it stopped at the same point every time.  I then used the Mini install and that worked.  However, after I rebooted I received the this error.  

Gave up waiting for root Common problems:
Boot args (cat /proc/cmdline)
Check rootdelay
Check root

ALERT! /dev/disk/by-uuid/bfaafj88-83ce-4dd2-8c6f-26o9a869eaea does not exists  Dropping into shell:

(initranfs)


I then reboot from this point by issuing the reboot command and can then go into the rescue login with networking.  I did select reconfigure GRUB and rebooted but same error as above.

Any suggestions?


System is an old Dell Poweredge 1550 
Ubuntu = 9.10 server

Thanks

Kurt

---

### Post by kurtwp on 2010-01-05
After doing some searching on this forum I came accross this command /etc/init.d/udev restart.  I reboot the server and logged into rescue and issued the following command "service udev stop" then "service udev start".  It appears that it fixed my issue.

Kurt

---

