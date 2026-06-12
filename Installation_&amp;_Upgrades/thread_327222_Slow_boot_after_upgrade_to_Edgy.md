---
title: "Slow boot after upgrade to Edgy"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by mons on 2006-12-28
Hi,
Just completed my upgrade from Dapper to Edgy.
All went well, but my boot now takes much longer to complete.  To me it looks like it hangs on LVM, but I am not sure.

Have a look at the attachment.  For about 3 minutes nothing seems to happen....

My system is installed on a dual boot with XP using a RAID-0 set using dmraid.  It worked fine and booted quickly in Dapper.  I have tried to disable the lvm in "sysv-rc-conf", but lvm still starts and looks like it is sleeping for 3 minutes for some reason.

Can anyone help or provide some pointers as to what migt be going on?  ](*,) 

Mons

---

### Post by Linki on 2006-12-30
Same problem here. But I don't have any clue what to do about.
It seems to hang on startup before all partions get mounted for about 3-4 minutes... very annoying since it worked fine with Dapper :-(

---

### Post by The Lance on 2007-01-04
I also have the same issue. For some reason my computer boots up slowy to I posted the boot png to see if anyone can see a proble,

---

### Post by mons on 2007-01-06
Hi Lance,
Looked at your chart.  Looks pretty quick compared to mine above....
I am starting to suspect a problem in dmraid, you are not running dmraid, are you Lance?

I have removed lvm2 and other lvm stuff from my machine, but the lvm process and the sleep still happens.  I also notice dmraid are using a mapper library that is also used by dmraid.  I have been searching for som configuration but no luck.
That annoying lvm process still starts and hang my boot for 3 minutes before it disappear and the boot continues.

Anyone have an idea?

Linki, are you using dmraid by any chance?

---

