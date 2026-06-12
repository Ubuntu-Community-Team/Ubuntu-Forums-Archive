---
title: "fdisk says my lvm2 hdd has no valid partition table"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by fedtobunt on 2011-12-11
I am new to ubuntu coming from fedora. 
Just installed ubuntu server and I can't mount my fedora LVM2 hdd. 
fdisk is saying the /dev/mapper/VG_DATA-LV_DATA doesn't contain a valid partition table for my /dev/sdc. The volume group only belongs to th sdc drive.
How do I mount it? What am  I missing?
See output below.
(Ignore sdb. That's part of old fedora raid install. I /dev/zero it but partitions still exist.)
BTW why did the installer install the lvm into to extended partition sd5? 


```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000731b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    78163967    38831105    5  Extended
/dev/sda5          501760    78163967    38831104   8e  Linux LVM

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcaadcaad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3068414     1534176   fd  Linux raid autodetect
/dev/sdb2         3068415     6136829     1534207+  82  Linux swap / Solaris
/dev/sdb3         6136830    78156224    36009697+  fd  Linux raid autodetect

Disk /dev/mapper/NAS1-root: 30.9 GB, 30870077440 bytes
255 heads, 63 sectors/track, 3753 cylinders, total 60293120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS1-root doesn't contain a valid partition table

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e141589

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001   8e  Linux LVM

Disk /dev/mapper/NAS1-swap_1: 935 MB, 935329792 bytes
255 heads, 63 sectors/track, 113 cylinders, total 1826816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/NAS1-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/VG_DATA-LV_DATA: 1099.5 GB, 1099511627776 bytes
255 heads, 63 sectors/track, 133674 cylinders, total 2147483648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/VG_DATA-LV_DATA doesn't contain a valid partition table

```

---

### Post by darkod on 2011-12-11
I haven't touched LVM much but I think everything is fine. It doesn't say /dev/sdc has no partition table, look more carefully, it detects that /dev/sdc has a single partition taking the whole disk and being LVM type.

The message about partition table seems to be for your logical volumes, and the LV doesn't have a separate partition table on itself anyway. It's equivalent to a partition if I'm not mistaken, partitions don't have tables, the disks do.

As for how to mount/open it, I'm not sure. Try googling for "how to mount or open existing LVM in ubuntu server" or similar.

---

### Post by darkod on 2011-12-11
As for why it installed in a logical partition, I guess you used the auto install option and that's how it does it not to use primary partitions (in case you are short on those).

This is the reason I always prefer manual partitioning when installing desktop or server. You have the control of the partitions, and you choose the type and size.

---

### Post by darkod on 2011-12-11
Quick search results:
[http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/](http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/)
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)
[http://serverfault.com/questions/36569/how-to-mount-a-lvm-partition-on-ubuntu](http://serverfault.com/questions/36569/how-to-mount-a-lvm-partition-on-ubuntu)

---

### Post by fedtobunt on 2011-12-11
OK got it mounted OK. thanks.
Now need to add groups with matching group ids as I am getting group IDS instead of group names.
drwxrwxr-x  3 root  **507**     4096 2008-02-11 00:36 Perfect

---

### Post by brf on 2011-12-11
Take a look at the "chgrp" or "chown" commands (do a "man chgrp" in a terminal window.)  You can go through the whole file structure and change the owner and/or group to one that works better for you:
# cd [head_directory_of_your_newly_mounted_file_system]
# chgrp -R root .

---

### Post by fedtobunt on 2011-12-13
Trying to copy the users from fedora t ubuntu
Anyone know what the . is after the permissions for last user?

drwx------   4  503  504 4096 2010-04-05 19:39 user1
drwx------   7  504  505 4096 2010-04-12 23:01 user2
drwx------   9 root root 4096 2011-11-19 16:22 user3
drwx------. 28  500  500 4096 2011-12-03 16:35 user4

---

