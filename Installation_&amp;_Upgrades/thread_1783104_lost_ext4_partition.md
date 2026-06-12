---
title: "lost ext4 partition"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by isthakur on 2011-06-15
Dear all
I had installed ubuntu on my 500GB harddisk and using it as local webserver and fileserver.
recently while running routine fsck there was a power cut and system turned off.
after restart the system reported grub error that invalid file system on root (/) 
I used live CD to trace the problem and launched gparted to  view the type of filesystem is displays unknown filesystem in front of the partition which was created using ext4 fs.
the patition contained lot of data and project works. 
could any one please help in recovering data from lost disk
i have tried using fsck as follows
sudo fsck /dev/sda1 -a
the system is waiting for more then 5 hrs with following message
file ??? (inode #12854463, modtime xxxx date and time xxx)
has 68000 multiply-claimed block(s), shared with 10 files:
..................................................
and few more lines
.....................................................

---

### Post by Quackers on 2011-06-15
Welcome to UF.
Have a look at this thread, it may give you some help, hopefully
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)

---

