---
title: "Oh my god i am finally making the switch!!! Need help!"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by DimitrisC on 2006-10-31
Ok i have been playing around with linux for quite sometime now but always came across some things that made me return to windows.  That was until i came across ubuntu (and specifically Ubuntu 6.06LTS Dapper Drake / I Tried edgy but too many bugs for me).  So i made a dual boot system and i now have a linux box that works great and set up the way i want it (i got everything that kept me away in the past working: xgl, ati, beryl, codecs, media players, plugins, everything....).

And now the question i have.  I am sure its a question not frequently ask in such forums.

As i mentioned i have a dual boot system.
This is the configuration as taken from gparted:

Partition     Filesystem   Size      Used       Unused      Flags
/dev/sda1       fat16     62.72MB   7.46MB      55.27MB
/dev/sda2       ntfs      55.00GB   30.54GB     24.46GB      boot

/dev/sda3      extended   19.47GB     ---         ---        lba
  /dev/sda5      fat32     3.57GB   812.93MB     2.78GB
  /dev/sda6   linux-swap  988.35MB    ---         ---
  /dev/sda7    reiserfs   14.93GB    7.46GB      7.47GB

sda1 corresponds to Dell Utility Partition
sda2 is the windows xp installation
sda5 was a fat partition to exchange files with linux

Grub is installed on the MBR as default

Is there a way to delete all other partitions and leave Linux as the main and only operating system on the computer and allocate all the free space remaining to the reiserfs partition where linux is installed.  By the i mean delete windows and all other partitions (sda1, sda5) and allocate the free space created to sda7 (linux partition) without destroying my linux installation???

I spent a lot of time tuning and setting up linux and i don't want to destroy it.

---

### Post by DimitrisC on 2006-11-01
Anyone???

---

### Post by bluenova on 2006-11-01
Yep, but you need to run gparted from a liveCD, because all the partitions have to be unmounted to delete and resize. Once you have gparted running from a livecd it's quite streight forward to delete the partitions and resize the ones that are left. Just remember to backup important data.

---

### Post by DimitrisC on 2006-11-02
Great!!! Thanks for your help! :-D

---

