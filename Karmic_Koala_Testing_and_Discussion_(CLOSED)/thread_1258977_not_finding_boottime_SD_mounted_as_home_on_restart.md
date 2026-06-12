---
title: "not finding boottime SD mounted as /home on restart"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by carolinecurran on 2009-09-05
I have a EeePC 700 that only has a 4GB Hard Drive to I've decided to have a 8GB as my /home directory unfortunately it comes up this if I restart(not shutdown> 
* Checking file systems...
869
fsck.ext4: Unable to resolve 'UUID=xxxxxxxx-xxxx-xxxx-xxx-xxxxxxxxx'
fsck died with exit status 8

*File system check failed .
A log file is being saved in /var/log/fsck/checkfs if that location is writeable
Please repair the file system manually .
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.

/var/log/fsck/checkfs gives
> Log of fsck -C3 -R -A -a
Sat Sep 5 23:34:00 2009

fsck from util-linux-ng 2.16
fsck.ext4: unable to resolve 'UUID=xxxxxxxx-xxxx-xxxx-xxx-xxxxxxxxx'
fsck died with  exit status 8

Sat Sep 5 23:34


yet interestingly "blkid" and "ls -l /dev/disk/by-uuid" both return the right uuid (also D5FD-F001 -> ../../sdb is also show as well as the two hard drives.

if I do a hard reset it works perfectly.

---

