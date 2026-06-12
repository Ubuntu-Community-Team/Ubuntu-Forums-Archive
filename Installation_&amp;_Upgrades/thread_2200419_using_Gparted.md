---
title: "using Gparted ?"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2014-01-19
ive run out of space in home directory
ive got a dual boot system windows/ubuntu 13.04
ive got 9 patitions
please see attachment

---

### Post by TheFu on 2014-01-19
A) no attachment.
B) please post the output of 
```
df -h
sudo parted -l
```
wrapped in "code" tags like I did, so things line up correctly. See "Adv Reply" button.

---

### Post by jimbean on 2014-01-19
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7       210G  6.6G  193G   4% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M   12K  992M   1% /dev
tmpfs           201M  916K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  160K 1001M   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda6       164M  2.7M  152M   2% /tmp
/dev/sda3       3.6G  2.4G  1.1G  70% /home
/dev/sda5       2.3G  131M  2.0G   7% /boot


Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  259GB  259GB   primary   ntfs            boot
 3      259GB   263GB  3948MB  primary   ext4
 2      263GB   500GB  237GB   extended
 7      263GB   491GB  228GB   logical   ext4
 8      491GB   497GB  6177MB  logical   linux-swap(v1)
 5      497GB   500GB  2500MB  logical   ext4
 6      500GB   500GB  181MB   logical   ext4

---

### Post by jimbean on 2014-01-19
```
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  259GB  259GB   primary   ntfs            boot
 3      259GB   263GB  3948MB  primary   ext4
 2      263GB   500GB  237GB   extended
 7      263GB   491GB  228GB   logical   ext4
 8      491GB   497GB  6177MB  logical   linux-swap(v1)
 5      497GB   500GB  2500MB  logical   ext4
 6      500GB   500GB  181MB   logical   ext4

```

---

### Post by jimbean on 2014-01-19
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7       210G  6.6G  193G   4% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M   12K  992M   1% /dev
tmpfs           201M  916K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  160K 1001M   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda6       164M  2.7M  152M   2% /tmp
/dev/sda3       3.6G  2.4G  1.1G  70% /home
/dev/sda5       2.3G  131M  2.0G   7% /boot

``````
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  259GB  259GB   primary   ntfs            boot
 3      259GB   263GB  3948MB  primary   ext4
 2      263GB   500GB  237GB   extended
 7      263GB   491GB  228GB   logical   ext4
 8      491GB   497GB  6177MB  logical   linux-swap(v1)
 5      497GB   500GB  2500MB  logical   ext4
 6      500GB   500GB  181MB   logical   ext4

```

---

### Post by Bashing-om on 2014-01-19
jimbean; Yuk;

Your ubuntu /home is very small (3948MB).
The best  option I can see is to shrink the Windows (NTFS) partition 1 - suggested to use Windows to do this (defrag X2, chkdsk)- and expand ubuntu's /home into that space (GParted).

Anytime one messes with (re-)partitioning there is the risk of LOSS of data ! In moving a partition to the left (header files) that risk is increased, Back up your data ! Be prepared to (RE-)install the operating systems.

Those with the greater experience may have a better alternative, but,

[INDENT][INDENT]that is what I would do
[/INDENT][/INDENT]

---

### Post by jimbean on 2014-01-19
so if i used gparted and deleted all of my partitions except for windows 
would windows still boot

---

### Post by TheFu on 2014-01-19
As stated by Bashing-om, changing partitions is risky, so it is best to have a full backup before starting.

It isn't that bad.  You have TONES of room in /, so you can easily merge /home under / and be done.  Also, the /boot partition is much larger than needed.  Just move the data in /home/* to /tmp-home/ to get started, edit the fstab to remove the /home partition, mv /tmp-home to /home and reboot. Order matters and I would be prepared when the OS freaks out that your $HOME is gone.  Make the amount of time where /home isn't there as small as possible.

Or you could backup your HOME (relatively small) and delete all the Linux partitions, then reinstall using a better learned-from-experience partitioning scheme.  Look at your current storage use and use that to plan the next iteration.  I would have /boot at least 1G, but not much larger.  I'd have / be 20G or so - room to install lots-o-programs and different desktops, swap would be 2G or the amount of RAM in the system, whatever is larger, then I'd probably drop 20G into /home with room to the right (in the disk layout) that is empty.  If you use lvm2, then adding more storage to any of these partitions later becomes much, much, much easier.

I should also point out that it is very possible to have 1 partition for swap and 1 partition for everything else - the 2nd one only 10-15G total.  I've been using the same desktop for many years and it is only 15G in size. Most "large data" is stored on the network. I do web-app server development in that amount of storage, plenty or room, unless you do java development. ;)

---

### Post by TheFu on 2014-01-19
forum error caused double-post..

---

### Post by jimbean on 2014-01-19
well it worked i deleted all of my partitions except windows partition with the gparted live cd

did not boot windows
installed ubuntu 13.10  used install along side windows option
and im back on 4 hrs later
windows vista boots and ubuntu 13.10 boots
thank for the morale support guys

---

### Post by Bashing-om on 2014-01-19
jimbean; Great !

all's well that ends well

[INDENT][INDENT]don't be a stranger
[/INDENT][/INDENT]

---

