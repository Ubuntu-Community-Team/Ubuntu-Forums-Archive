---
title: "problem with space"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by jordan2410 on 2009-12-22
hi,i m new in ubuntu 9.4 and there seems to be a little problem with the disk space...while i have 40 gb free,when i try to download and install something it says that i have to clear some space...any help appreciated

---

### Post by Dunatotatos on 2009-12-22
Hi,

Can you give us more details ? Like the download tried, if you have your /home on a separated partition, (if you don't know, it's probably not). Ubuntu is used on a LiveCD / LiveUSB or installed on the hard disk ?

---

### Post by jordan2410 on 2009-12-22
i tried to download flash player for ubuntu and it sayed these: install: writing `/usr/lib/flashplugin-installer/libflashplayer.so': No space left on device
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: No space left on device
it does the same for other files too.i don't think i have separated partition(i don't know),and ubuntu is installed on the hard disk

---

### Post by Dunatotatos on 2009-12-22
Hum, very strange. Have you glance in the Analyzer of use of disks (into Applications >> Accessories) ?

You said that you have 40 Gb free. How do you know it ? It's an indication of Ubuntu ?

---

### Post by phillw on 2009-12-22
Hi,

Can you post the output of ```
 df -h
```

Thanks,

Phill.

---

### Post by drs305 on 2009-12-22
Welcome to Ubuntu and the Ubuntu forums.

Is this by chance a new install of Jaunty, using the "side by side with Windows" option? If so, there was a bug that made the partition too small. If that was the case, you may want to look at [HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

Take a look at this guide:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

It would also help out if you posted the results of:
```

df -h

```

---

### Post by jordan2410 on 2009-12-22
well it says that the total filesystem capacity is 2.3 gb and it's full..but yes i checked in the hard disk properties and it said that i had 40gb free

---

### Post by drs305 on 2009-12-22
> **jordan2410 said:**
> well it says that the total filesystem capacity is 2.3 gb and it's full..but yes i checked in the hard disk properties and it said that i had 40gb free

That's the bug I referred to. See the first link in my previous post on how to solve it. You basically can reinstall or steal space from Windows. The choice is yours and they will probably take about the same amount of time.

---

### Post by phillw on 2009-12-22
> **jordan2410 said:**
> well it says that the total filesystem capacity is 2.3 gb and it's full..but yes i checked in the hard disk properties and it said that i had 40gb free

Hi, it's called 

2.3GB hell...... yeah, head over to the link drs posted, above to get yourself up & running.

Regards,

Phill.

---

### Post by jordan2410 on 2009-12-22
these are the results of df-h.yes i have side by side with windows

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2,3G  2,3G     0 100% /
tmpfs                 1,5G     0  1,5G   0% /lib/init/rw
varrun                1,5G  104K  1,5G   1% /var/run
varlock               1,5G     0  1,5G   0% /var/lock
udev                  1,5G  156K  1,5G   1% /dev
tmpfs                 1,5G  492K  1,5G   1% /dev/shm
lrm                   1,5G  2,4M  1,5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1,0M   16K 1008K   2% /tmp

---

### Post by phillw on 2009-12-22
Confirmed as 2.3GB 'bug'

Follow the instructions in post #7, or just do a fresh install, but select manual partitioning to give the ubuntu area more room (10GB is recommended for most users, unless you're planning on keeping loads of music / videos on there)

Regards,

Phill.

---

### Post by jordan2410 on 2009-12-22
thank you very much!i will try it as soon as possible

---

