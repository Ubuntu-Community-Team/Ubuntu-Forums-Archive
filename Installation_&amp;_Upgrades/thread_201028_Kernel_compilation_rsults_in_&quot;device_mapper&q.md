---
title: "Kernel compilation rsults in &quot;device mapper&quot; errors"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2006-06-21
Hi,
I tried to compile a new kernel (2.6.17.1) on my Kubuntu Dapper.
After reboot everything is OK (I currently use this kernel) except for multiple "device mapper" errors (See below). I've searched the forums and googled and found that it is probably related to RAID and/or EVMS support.

However, I've configured (and actually re-verified and re-compiled the kernel with the same results) that the kernel was configured with full RAID support; yet, I could **not** find where the EVMS option "hides" (I used make xconfig).

Please advise and clarify the implications of my current kernel.

TIA :o 

---------output of relevant dmesg segment -------------
[4294688.043000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[4294688.837000] device-mapper: dm-linear: Device lookup failed
[4294688.837000] device-mapper: error adding target to table
[4294688.839000] device-mapper: dm-linear: Device lookup failed


Note: the last 2 lines repeat multiple times !
--------------end-----------

---

### Post by chimarathonx5 on 2006-06-23
I do not want to admit to how much time I wasted on this one but, the answer for me was very simple.  I just figured it out 5 mimutes ago.  If you are up and running and all is well tell evms to FOAD like I did

update-rc.d  -f evms remove



then reboot to a happy kernel 

I figured it out after i was playing around with the init scripts and got the error while on a live os that i was able to view partitions on.  Any who, its late and I played with this error for days.  (darn long recompiles)


Here is a little more info on evms.  This gives a more lengthy workaround but, and explains how evms tries to claim the partition that evms already claimed.  

[http://evms.sourceforge.net/faq.html](http://evms.sourceforge.net/faq.html)
I

---

### Post by mibadt on 2006-06-24
Thanks, The key was indeed EVMS.
I followed the recommendations in the EVMS page namely:
1. modified my fstab: each entry was modified /dev/xxx-->/dev/evms/xxx
2. modified the kubuntu entry in my (grub's) menu.lst the same way.
and rebooted into a flawless kernel !
;) 

[QUOTE=chimarathonx5]I do not want to admit to how much time I wasted on this one but, the answer for me was very simple.  I just figured it out 5 mimutes ago.  If you are up and running and all is well tell evms to FOAD like I did

update-rc.d  -f evms remove



then reboot to a happy kernel 

I figured it out after i was playing around with the init scripts and got the error while on a live os that i was able to view partitions on.  Any who, its late and I played with this error for days.  (darn long recompiles)


Here is a little more info on evms.  This gives a more lengthy workaround but, and explains how evms tries to claim the partition that evms already claimed.  

[http://evms.sourceforge.net/faq.html](http://evms.sourceforge.net/faq.html)
I[/QUOTE]

---

