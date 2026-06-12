---
title: "Missing drive?.?.?"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by holeyshoe on 2007-03-19
Just installed ubuntu, restarted my pc, loaded windows - everything was fine couldnt see the ubuntu drive as  is expected. Restarted again, loaded Ubuntu. Now heres the problem, the windows drive cant be seen at all. It's a Sata drive and my Ubuntu is an IDE drive. partition tables are as follows:

major minor  #blocks  name

   8     0  245117376 sda
   8     1  245111706 sda1
   3    64   80043264 hdb
   3    65   77039676 hdb1
   3    66          1 hdb2
   3    69    2996091 hdb5

Could someone please tell a newbie like me how I can get to sda or sda1 which ever is my windows drive? I cant cd to it or surf to it in the file browser. It shows up in the partition tables but for all other pruposes it's missing.

---

### Post by louieb on 2007-03-19
Don't know about Edgy but if you use Dapper try System>Administration>Disk. 
Click on a disk then open the partition tab and  if it has an enable button click it and see what happens.

BTW: how did you get  that partition table list? Never seen anything like it. 
If the above does not work open Applications>Accessories>Terminal and copy/paste  the output from ```
sudo fdisk -l
``` (l as in little), here.

---

### Post by holeyshoe on 2007-03-20
Tried the system > admin > disk, doesnt work in Edgy, sadly there is no disk option in the admin menu.

I ran the command you posted and got this:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9591    77039676   83  Linux
/dev/hdb2            9592        9964     2996122+   5  Extended
/dev/hdb5            9592        9964     2996091   82  Linux swap / Solaris

I got the partition data by running: cat /proc/partitions

---

### Post by louieb on 2007-03-20
> **holeyshoe said:**
> I got the partition data by running: cat /proc/partitions
I learn something new every day. Now I need to find out what the columns are?

The psychocats link in my signature has a page on how to mount windows in Ubuntu. (as well as pages on other stuff you might want to do). 
and [this is what I use to Read EXT3 partition]("http://www.fs-driver.org/")(s)  when using windows.

There both straight forward and that should get you set up.

---

### Post by holeyshoe on 2007-03-20
Thanks, I'll check out those links when  get home tonight.

*edit* Sweet, just added the line
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
from the mounting windows tutorial on the site, mounted it and it, runs like magic!

Thank you very much m8!

---

