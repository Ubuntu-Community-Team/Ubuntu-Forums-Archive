---
title: "Having problems with partitions for a new windows space."
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by jellyxbean on 2010-10-19
I have been trying to put windows onto my system as I made the switch to full linux awhile ago, but the need for  certain windows programs is obviously tough to break.

df -h
--------------------------
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   59G   79G  43% /
udev                  498M  260K  497M   1% /dev
none                  498M   76K  498M   1% /dev/shm
none                  498M  200K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw


fdisk -l
-----------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92e4538c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solari

I am posting this information because in the other topics I have seen they always asked for them. Whenever I use Gparted though there are no options for me to make a new partition all the options are basically greyed out and I have even tried using it from gksudo.

I am on an EEEpc and cant really do much from the way of live cd's as I have seen in other topics as well.

---

### Post by oldfred on 2010-10-19
You cannot edit partitions that are mounted, so you cannot use a gparted from your Linux install. You have to boot from a liveCD or if no CD use a liveUSB flash drive and probably still have to unmount (swapoff) the swap partition.

You will have to shrink sda1 and create a new sda3 as NTFS with the boot flag. Do not put the new partition in the extended partition as the first install of windows only works from primary partitions.

---

### Post by jellyxbean on 2010-10-19
Will this shrinking which I am assuming is resizing it? would this resizing of the partition make me lose any data? I was only going to give the windows partition enough to be installed and run Itunes and a game program since that is all I need it for.

---

### Post by oldfred on 2010-10-19
You do not want to make a NTFS partition too small, it needs about 20-30% free space or it slows down or stops working as it does not have space to write files. Of course any partition changes have risk so you should have good backups.

---

