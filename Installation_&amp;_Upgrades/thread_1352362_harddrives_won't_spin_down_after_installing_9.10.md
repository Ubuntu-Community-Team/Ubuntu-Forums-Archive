---
title: "harddrives won't spin down after installing 9.10"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by newstome on 2009-12-11
I just installed 9.10 on a new hard drive and cannot get the my other hard drive to spin down. This worked fine on 9.04.
 
This is what I did on 9.04:
 
hdparm -S 240 /dev/sdb
 
Drive would spin down after 20 minutes or so...
 
running hdparm -C /dev/sdb would show the drive was in standby mode
 
The same no longer works.
 
Now, the drive always is spun up and hdparm -C shows active/idle
 
I have even unmounted the drive to make sure there were no active file handles and get the same behavior.
 
Where can I go to investigate this further?

---

### Post by _Dave03_ on 2010-03-05
Same for me running Ubutnu Server 9.10.

hdparm -Y /dev/sdb

and

hdparm -y /dev/sdb

works for me. The drives wake up correctly, too.

But triggering it using

hdparm -S 1 /dev/sdb

won't do is job. (Will never go to sleep/standby)

There's noting accessing the drive(it's empty).

Any suggestions?

Regards,

Dave

---

