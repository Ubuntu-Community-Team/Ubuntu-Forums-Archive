---
title: "sdb1 drive missing in Ubuntu 8.10"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by carusoswi on 2008-10-23
So, I've run 8.10 for a few weeks, now.  In the last couple of days, upon boot, the desktop appears, and my drives - sda, three external drives, cdrom, all show up.  But the slave drive which Ubuntu refers to as sdb1 doesn't post up to the desktop.

If I explore 'places', then 'file system', then 'media', there is a listing for sdb1, but checking its properties returns a message that it is empty and the folder is described as 'inode/directory'.

I can boot into XP and this directory shows up and can be accessed normally.

What might have happened?

Is this some sort of issue with the alpha 8.10 that I just need to be patient with, or is something else going on?

Caruso

---

### Post by henwyn on 2008-10-23
Is the drive listed in /etc/fstab?

---

### Post by henwyn on 2008-10-23
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=956359&highlight=%2Fetc%2Ffstab](http://ubuntuforums.org/showthread.php?t=956359&highlight=%2Fetc%2Ffstab) which shows how to deal with a similar problem in Xubuntu.

---

