---
title: "Fresh Install"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by ktechman on 2008-11-20
I need to do a fresh install of Intrepid because of various mistakes I made in the upgrade process. I have all pertinent information backed up. I need to preserve two SATA drives that are marked  /data1 and /data3 in /etc/fstab. After the install can I just reinsert the information from the current fstab file or is there something else I need to do? Also when I do the partitioning will the installer just ignore the hard drives? Thank you for your reply
Ktechman

---

### Post by Pumalite on 2008-11-20
When you install; you have to choose where you want Ubuntu to install by going 'Manual'. Think about your fstab after the installation is complete. If you post:
sudo fdisk -lu
It would help others to help you.

---

### Post by ktechman on 2008-11-20
Here it is:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39b79b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16016804     8008371   82  Linux swap / Solaris
/dev/sda2        16016805   488392064   236187630   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a7273

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    16016804     8008371   82  Linux swap / Solaris
/dev/sdb2        16016805   976768064   480375630   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf42bf42b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    83971754    41985846    7  HPFS/NTFS
/dev/sdc2        83971755    99988559     8008402+  82  Linux swap / Solaris
/dev/sdc3        99988560   148810094    24410767+  83  Linux
/dev/sdc4       148810095   312576704    81883305    5  Extended
/dev/sdc5       148810158   168827084    10008463+  83  Linux
/dev/sdc6       168827148   198900764    15036808+  83  Linux
/dev/sdc7       198900828   312576704    56837938+  83  Linux

```  Thank you for your help Pumalite.

Ktechman

---

### Post by Coreigh on 2008-11-20
The output shows you have 3 disks, sda 250gb, sdb 500gb and sdc 160gb.

Take note from your current fstab where data2 and data3 are mounted. Are they sda sdb or sdc. Print or save a copy of your fstab somewhere for reference (and any other files or config setting you want to re-create) When you do your install choose Manual at the partitioning and make sure that the sdx's where data2 and data3 are do NOT get formatted. You can if you want to create mount points for them during the install but you will probably feel safer completing the install and then re-attaching the drives.

Do you have multiple installs of Linux? it looks like all three disks have a primary and a swap partition. Are you re-installing on sdc, the 160gb disk? I am guessing that sdc2 is the / partition, sdc3 is swap and sdc5, sdc6, and sdc7 are your data partitions. Is 5, 6, 0r 7 your /home or /var?

To make an example; Do the install mount sdc2 as / and format, sdc3 as swap and then do not mount or format 5, 6, or 7. If one of those is your /home (or other) you can re-attach it just the same as you will your data partitions.

---

### Post by ktechman on 2008-11-21
You are correct in your assumptions about the partitions.  To reattach the disk so they are auto mounted at boot do I just re-enter the information that was present, about sda and sdb in the previous fstab, into my present fstab?

---

