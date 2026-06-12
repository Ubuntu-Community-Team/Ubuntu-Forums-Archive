---
title: "Partition help"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by Adam Boettiger on 2004-11-04
Really basic question, but I can't find the answer in any of the FAQ's on the Ubuntu site:

How many partitions, what names and what recommended sizes?

/ - 2GB
/swap - 512MB
/NewWorld - 1GB*
/Home - Rest of storage

??

Or is a better idea just to let the installer auto-partition the free space?

There is a HowTo on the Ubuntu site that talks about doing a PowerPC/Mac install and says to label a partition "NewWorld" but no size recommendations at all.

Help!

---

### Post by p!=f on 2004-11-04
I like to have plenty of partitions so I can mount them with non-default options (ie. /var/log with nosuid,nodev,noexec options) :).
Here's my setup.

> 
 * 00:33:43 * pef @ agonicus *
[~] > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             228M  120M   97M  56% /
tmpfs                 380M   12K  380M   1% /dev/shm
shm                   380M   12K  380M   1% /dev/shm
/dev/hda7              67M   14M   49M  23% /boot
/dev/hda14            2,8G  1,9G  770M  72% /home
/dev/hda4              32G   15G   16G  49% /home/store
/dev/hdb2              32G  2,0G   28G   7% /home/store/audio
/dev/hdb3              38G   33G  3,2G  92% /home/store/video
/dev/hda11            3,3G   67M  3,0G   3% /opt
/dev/hdb1             5,1G  2,0G  2,9G  40% /opt/games
/dev/hda15            221M  4,4M  205M   3% /root
/dev/hda13            456M  9,1M  423M   3% /tmp
/dev/hda12            4,8G  2,4G  2,2G  52% /usr
/dev/hda9             1,8G  154M  1,6G   9% /var
/dev/hda10            228M   49M  167M  23% /var/log

+ 1GB swap partition (2x RAM but more than a giga is not recommended).


---

### Post by fng on 2004-11-04
a good default noobie setup is :
/dev/hda1 +-25MB /boot (ext2/3)
/dev/hda2 2xRAM swap
/dev/hda3 all_the_rest / (ext3/reiserfs)

Don't let /boot automount on startup.  So you wont accidentually overwrite it (like in 'a hacker can't mess with it'), and your system will always boot :).

---

